# utl-python-applying-sas-formats-located-in-external-sas-catalogs-to-imported-sas-tables
Python applying sas formats located in an external sas catalog to imported sas tables 

                                                                                                                                        
    Python applying sas formats located in an external sas catalog to imported sas tables                                               
                                                                                                                                        
    convert a sas table to a panda datafrom and apply sas formats located in a external sas cataloG.                                    
                                                                                                                                        
      Convert "M" to "Male" and "F" to "Female in                                                                                       
                                                                                                                                        
    github                                                                                                                              
    https://tinyurl.com/y66dgr4t                                                                                                        
    https://github.com/rogerjdeangelis/utl-python-applying-sas-formats-located-in-external-sas-catalogs-to-imported-sas-tables          
                                                                                                                                        
    *_                   _                                                                                                              
    (_)_ __  _ __  _   _| |_                                                                                                            
    | | '_ \| '_ \| | | | __|                                                                                                           
    | | | | | |_) | |_| | |_                                                                                                            
    |_|_| |_| .__/ \__,_|\__|                                                                                                           
            |_|                                                                                                                         
    ;                                                                                                                                   
                                                                                                                                        
    libname fmt "d:/fmt";                                                                                                               
    proc format lib=fmt.formats;                                                                                                        
      value $sex                                                                                                                        
        "M" = "Male"                                                                                                                    
        "F" = "Female"                                                                                                                  
    ;quit;                                                                                                                              
                                                                                                                                        
    options validvarname=upcase;                                                                                                        
    libname sd1 "d:/sd1";                                                                                                               
    data sd1.have;                                                                                                                      
      set sashelp.class(obs=4);                                                                                                         
      format sex $sex.;                                                                                                                 
    run;quit;                                                                                                                           
                                                                                                                                        
    SAS INPUT TABLE                                                                                                                     
    ===============                                                                                                                     
                                                                                                                                        
    d:/sd1/have.sas7bdat                                                                                                                
                                                                                                                                        
    SD1.HAVE total obs=4                                                                                                                
                                                                                                                                        
    Obs     NAME      SEX    AGE    HEIGHT    WEIGHT                                                                                    
                                                                                                                                        
     1     Alfred      M      14     69.0      112.5                                                                                    
     2     Alice       F      13     56.5       84.0                                                                                    
     3     Barbara     F      13     65.3       98.0                                                                                    
     4     Carol       F      14     62.8      102.5                                                                                    
                                                                                                                                        
     Variable    Type    Len    Format                                                                                                  
                                                                                                                                        
     NAME        Char      8                                                                                                            
     SEX         Char      1    $SEX.                                                                                                   
     AGE         Num       8                                                                                                            
     HEIGHT      Num       8                                                                                                            
     WEIGHT      Num       8                                                                                                            
                                                                                                                                        
                                                                                                                                        
    FORMAT CATALOG                                                                                                                      
    ==============                                                                                                                      
                                                                                                                                        
    d:/fmt/formats.sas7bcat                                                                                                             
                                                                                                                                        
                                                                                                                                        
     --- Record Number ---  1   ---  Record Length ---- 80                                                                              
                                                                                                                                        
    ...............c..........1...."".33..2..............."".33..2.3.#3...........                                                    
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...8                                                    
    000000000000CE86B11CB9000C381111220330030000000000001111220330030302300001000000                                                    
    0000000000002A13341FD280971C8F01220331224000000000318F01220331224313300000310000                                                    
                                                                                                                                        
                                                                                                                                        
     --- Record Number ---  2   ---  Record Length ---- 80                                                                              
                                                                                                                                        
    ....SAS FILEFORMATS                         ................................CATA                                                    
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...8                                                    
    00005452444444544552222222222222222222222222000000000000000000000000000000004454                                                    
    0000313069C56F2D1430000000000000000000000000000000000000000000000000000000003141                                                    
                                                                                                                                        
    ....                                                                                                                                
                                                                                                                                        
     --- Record Number ---  64   ---  Record Length ---- 80                                                                             
                                                                                                                                        
    ....................`.......FORMATC SEX.................................8.......                                                    
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...8                                                    
    00000000000000000000601000004454454254500000000000000000000000000000000030000000                                                    
    00000000000000002000030800006F2D143035800000000000000000000000000000200084030000                                                    
                                                                                                                                        
                                                                                                                                        
                                                                                                                                        
                                                                                                                                        
                                                                                                                                        
     --- Record Number ---  170   ---  Record Length ---- 80                                                                            
                                                                                                                                        
    ..........M               ..........Male...........Female.......................                                                    
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...8                                                    
    000000001042222222222222220000000000466600000000000466666000000FFFF0000000000F00                                                    
    000000B040D0000000000000005090006040D1C5050B000606065D1C5000000FFFF00004000F11E0                                                    
                                                                                                                                        
                                                                                                                                        
    *            _               _                                                                                                      
      ___  _   _| |_ _ __  _   _| |_                                                                                                    
     / _ \| | | | __| '_ \| | | | __|                                                                                                   
    | (_) | |_| | |_| |_) | |_| | |_                                                                                                    
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                                   
                    |_|                                                                                                                 
     _ __   __ _ _ __   __| | __ _                                                                                                      
    | '_ \ / _` | '_ \ / _` |/ _` |                                                                                                     
    | |_) | (_| | | | | (_| | (_| |                                                                                                     
    | .__/ \__,_|_| |_|\__,_|\__,_|                                                                                                     
    |_|                                                                                                                                 
         _       _         __                                                                                                           
      __| | __ _| |_ __ _ / _|_ __ __ _ _ __ ___   ___                                                                                  
     / _` |/ _` | __/ _` | |_| '__/ _` | '_ ` _ \ / _ \                                                                                 
    | (_| | (_| | || (_| |  _| | | (_| | | | | | |  __/                                                                                 
     \__,_|\__,_|\__\__,_|_| |_|  \__,_|_| |_| |_|\___|                                                                                 
                                                                                                                                        
    ;                                                                                                                                   
                                                                                                                                        
    Note Sex is formatted                                                                                                               
                                                                                                                                        
    Python pada dataframe WANT                                                                                                          
                                                                                                                                        
        NAME     SEX   AGE  HEIGHT  WEIGHT                                                                                              
      Alfred    Male  14.0    69.0   112.5                                                                                              
       Alice  Female  13.0    56.5    84.0                                                                                              
     Barbara  Female  13.0    65.3    98.0                                                                                              
       Carol  Female  14.0    62.8   102.5                                                                                              
                                                                                                                                        
    I aslo sent the formmated vesion back to SAS                                                                                        
                                                                                                                                        
                                                                                                                                        
                                                                                                                                        
    WORK.WANT total obs=4                                                                                                               
                                                                                                                                        
       NAME       SEX      AGE    HEIGHT    WEIGHT                                                                                      
                                                                                                                                        
      Alfred     Male       14     69.0      112.5                                                                                      
      Alice      Female     13     56.5       84.0                                                                                      
      Barbara    Female     13     65.3       98.0                                                                                      
      Carol      Female     14     62.8      102.5                                                                                      
                                                                                                                                        
                                                                                                                                        
                                                                                                                                        
    #    Variable    Type    Len                                                                                                        
                                                                                                                                        
    1    NAME        Char      7                                                                                                        
    2    SEX         Char      6  ** original length was 1                                                                              
    3    AGE         Num       8                                                                                                        
    4    HEIGHT      Num       8                                                                                                        
    5    WEIGHT      Num       8                                                                                                        
                                                                                                                                        
    *                                                                                                                                   
     _ __  _ __ ___   ___ ___  ___ ___                                                                                                  
    | '_ \| '__/ _ \ / __/ _ \/ __/ __|                                                                                                 
    | |_) | | | (_) | (_|  __/\__ \__ \                                                                                                 
    | .__/|_|  \___/ \___\___||___/___/                                                                                                 
    |_|                                                                                                                                 
    ;                                                                                                                                   
                                                                                                                                        
    %utl_submit_py64_37("                                                                                                               
    import pandas as pd;                                                                                                                
    import pyreadstat;                                                                                                                  
    want, meta = pyreadstat.read_sas7bdat('d:/sd1/have.sas7bdat', catalog_file='d:/fmt/formats.sas7bcat', formats_as_category=True);    
    print(want);                                                                                                                        
    pyreadstat.write_xport(want, 'd:/xpt/want.xpt',table_name='want');                                                                  
    ");                                                                                                                                 
                                                                                                                                        
    libname xpt xport "d:/xpt/want.xpt";                                                                                                
    proc contents data=xpt._all_;                                                                                                       
    run;quit;                                                                                                                           
    data want;                                                                                                                          
      set xpt.want;                                                                                                                     
    run;quit;                                                                                                                           
    libname xpt clear;                                                                                                                  
                                                                                                                                        
                                                                                                                                        
