# utl-calculate-the-eigenvalues-of-a-matrix
Calculate the eigenvalues of a matrix

    Calculate the eigenvalues of a matrix                                                                                        
                                                                                                                                 
    github                                                                                                                       
    https://tinyurl.com/rfo23pm                                                                                                  
    https://github.com/rogerjdeangelis/utl-calculate-the-eigenvalues-of-a-matrix                                                 
                                                                                                                                 
    SAS Forum                                                                                                                    
    https://tinyurl.com/rcpqhxb                                                                                                  
    https://communities.sas.com/t5/SAS-IML-Software-and-Matrix/How-to-compute-Eigen-Values-without-using-CALL-EIGEN/m-p/610178   
                                                                                                                                 
    Zaynab                                                                                                                       
    https://stackoverflow.com/users/4189667/zaynab                                                                               
    https://stackoverflow.com/questions/30691990/eigenvalues-and-eigenvectors-in-r                                               
    *_                   _                                                                                                       
    (_)_ __  _ __  _   _| |_                                                                                                     
    | | '_ \| '_ \| | | | __|                                                                                                    
    | | | | | |_) | |_| | |_                                                                                                     
    |_|_| |_| .__/ \__,_|\__|                                                                                                    
            |_|                                                                                                                  
    ;                                                                                                                            
    options validvarname=upcase;                                                                                                 
    libname sd1 "d:/sd1";                                                                                                        
    data sd1.have;                                                                                                               
    input v1-v4;                                                                                                                 
    cards4;                                                                                                                      
     0.6 -0.1 -0.5  0.0                                                                                                          
    -0.1  1.0  0.0 -0.9                                                                                                          
    -0.5  0.0  1.0 -0.5                                                                                                          
     0.0 -0.9 -0.5  1.4                                                                                                          
    ;;;;                                                                                                                         
    run;quit;                                                                                                                    
                                                                                                                                 
    SD1.HAVE total obs=4                                                                                                         
                                                                                                                                 
      V1      V2      V3      V4                                                                                                 
                                                                                                                                 
      0.6    -0.1    -0.5     0.0                                                                                                
     -0.1     1.0     0.0    -0.9                                                                                                
     -0.5     0.0     1.0    -0.5                                                                                                
      0.0    -0.9    -0.5     1.4                                                                                                
                                                                                                                                 
    *            _               _                                                                                               
      ___  _   _| |_ _ __  _   _| |_                                                                                             
     / _ \| | | | __| '_ \| | | | __|                                                                                            
    | (_) | |_| | |_| |_) | |_| | |_                                                                                             
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                            
                    |_|                                                                                                          
    ;                                                                                                                            
                                                                                                                                 
    work.VECTORS total obs=4                                                                                                     
                                                                                                                                 
    Obs       V1          V2          V3        V4                                                                               
                                                                                                                                 
     1      0.13598     0.52054     0.67863    -0.5                                                                              
     2     -0.54126     0.38531    -0.55549    -0.5                                                                              
     3     -0.34800    -0.74471     0.27257    -0.5                                                                              
     4      0.75329    -0.16115    -0.39572    -0.5                                                                              
                                                                                                                                 
                                                                                                                                 
    Work.VALUES total obs=4                                                                                                      
                                                                                                                                 
    Obs    EIGEN_HA                                                                                                              
                                                                                                                                 
     1      2.27767                                                                                                              
     2      1.24130                                                                                                              
     3      0.48103                                                                                                              
     4     -0.00000                                                                                                              
                                                                                                                                 
    *                                                                                                                            
     _ __  _ __ ___   ___ ___  ___ ___                                                                                           
    | '_ \| '__/ _ \ / __/ _ \/ __/ __|                                                                                          
    | |_) | | | (_) | (_|  __/\__ \__ \                                                                                          
    | .__/|_|  \___/ \___\___||___/___/                                                                                          
    |_|                                                                                                                          
    ;                                                                                                                            
                                                                                                                                 
    %utl_submit_r64('                                                                                                            
    library(haven);                                                                                                              
    library(SASxport);                                                                                                           
    library(data.table);                                                                                                         
    have<-as.matrix(read_sas("d:/sd1/have.sas7bdat"));                                                                           
    vectors<-as.data.frame(eigen(have)$vectors);                                                                                 
    values<-as.data.frame(eigen(have)$values);                                                                                   
    write.xport(vectors,values,file="d:/xpt/want.xpt");                                                                          
    ');                                                                                                                          
                                                                                                                                 
    libname xpt xport "d:/xpt/want.xpt";                                                                                         
    data vectors;                                                                                                                
      set xpt.vectors;                                                                                                           
    run;quit;                                                                                                                    
    data values;                                                                                                                 
      set xpt.values;                                                                                                            
    run;quit;                                                                                                                    
    libname xpt clear;                                                                                                           
                                                                                                                                 
                                                                                                                                 
                                                                                                               
