# utl_maximum_length_csv_fields
Max length of each field in a CSV(coma delimited file) before importing (IML/R - WPS/Proc R)

    ```  Max length of each field in a CSV(coma delimited file) before importing (IML/R - WPS/Proc R)  ```
    ```  You need to download the free version of WPS. Free version doesn not limit size of output SAS dataset  ```
    ```      WORKING CODE  ```
    ```        IML/R    WPS/PROC R  ```
    ```    ```
    ```         file_path <- "d:/csv/shoes.csv";  ```
    ```         have <- fread(file_path, colClasses = "character");  ```
    ```         want<-sapply(have, function(x) max(nchar(x)));  ```
    ```    ```
    ```    ```
    ```  see  ```
    ```  https://goo.gl/AFYQoA  ```
    ```  https://stackoverflow.com/questions/30696776/calculate-max-length-of-each-field-in-csv-file  ```
    ```    ```
    ```  Michelle profile  ```
    ```  https://stackoverflow.com/users/1759974/michele  ```
    ```    ```
    ```  Perl might be the fastest solution, but R data table should suffice.  ```
    ```    ```
    ```    ```
    ```  HAVE  ```
    ```  ====  ```
    ```    ```
    ```  D:/CSV/SHOES.CSV  ```
    ```    ```
    ```    ```
    ```  REGION,PRODUCT,SUBSIDIARY,STORES,SALES,INVENTORY,RETURNS  ```
    ```    ```
    ```  Africa,Slipper,Addis Ababa,14,"$68,641","$279,795","$1,771"  ```
    ```  Africa,Sport Shoe,Addis Ababa,4,"$1,690","$16,634",$79  ```
    ```  Africa,Women's Casual,Addis Ababa,2,"$51,541","$98,641",$940  ```
    ```  Africa,Women's Dress,Addis Ababa,12,"$108,942","$311,017","$3,233"  ```
    ```  Africa,Boot,Algiers,21,"$21,297","$73,737",$710  ```
    ```  Africa,Sport Shoe,Johannesburg,8,"$5,172","$29,368",$139  ```
    ```  Africa,Women's Dress,Johannesburg,4,"$42,682","$120,127",$966  ```
    ```  Africa,Boot,Khartoum,24,"$19,282","$105,370",$700  ```
    ```  Central America/Caribbean,Women's Casual,San Juan,10,"$104,420","$318,207","$4,240"  ```
    ```    ```
    ```    ```
    ```    ```
    ```  WANT  ```
    ```  ====  ```
    ```    ```
    ```  Up to 40 obs from wantwps total obs=7  ```
    ```    ```
    ```  Obs    VAR           LEN  ```
    ```    ```
    ```   1     REGION        25  ```
    ```   2     PRODUCT       14  ```
    ```   3     SUBSIDIARY    12  ```
    ```   4     STORES        2  ```
    ```   5     SALES         10  ```
    ```   6     INVENTORY     10  ```
    ```   7     RETURNS       7  ```
    ```    ```
    ```  *                _              _       _  ```
    ```   _ __ ___   __ _| | _____    __| | __ _| |_ __ _  ```
    ```  | '_ ` _ \ / _` | |/ / _ \  / _` |/ _` | __/ _` |  ```
    ```  | | | | | | (_| |   <  __/ | (_| | (_| | || (_| |  ```
    ```  |_| |_| |_|\__,_|_|\_\___|  \__,_|\__,_|\__\__,_|  ```
    ```    ```
    ```  ;  ```
    ```    ```
    ```  dm "dexport sashelp.shoes 'd:/csv/shoes.csv' replace";  ```
    ```    ```
    ```  *          _       _   _  ```
    ```   ___  ___ | |_   _| |_(_) ___  _ __  ```
    ```  / __|/ _ \| | | | | __| |/ _ \| '_ \  ```
    ```  \__ \ (_) | | |_| | |_| | (_) | | | |  ```
    ```  |___/\___/|_|\__,_|\__|_|\___/|_| |_|  ```
    ```    ```
    ```  ;  ```
    ```    ```
    ```  proc datasets lib=work kill;  ```
    ```  run;quit;  ```
    ```    ```
    ```  %utl_submit_wps64('  ```
    ```  options set=R_HOME "C:/Program Files/R/R-3.4.0";  ```
    ```  libname wrk sas7bdat "%sysfunc(pathname(work))";  ```
    ```  proc r;  ```
    ```  submit;  ```
    ```  source("C:/Program Files/R/R-3.4.0/etc/Rprofile.site", echo=T);  ```
    ```  library(data.table);  ```
    ```  file_path <- "d:/csv/shoes.csv";  ```
    ```  have <- fread(file_path, colClasses = "character");  ```
    ```  want<-sapply(have, function(x) max(nchar(x)));  ```
    ```  want<-as.data.frame(cbind(names(want),want));  ```
    ```  colnames(want)<-c("VAR","LEN");  ```
    ```  want;  ```
    ```  endsubmit;  ```
    ```  import r=want data=wrk.wantwps;  ```
    ```  run;quit;  ```
    ```  ');  ```
    ```    ```
    ```  proc print data=wantwps;  ```
    ```  run;quit;  ```
    ```    ```
    ```  Obs    VAR           LEN  ```
    ```    ```
    ```   1     REGION        25  ```
    ```   2     PRODUCT       14  ```
    ```   3     SUBSIDIARY    12  ```
    ```   4     STORES        2  ```
    ```   5     SALES         10  ```
    ```   6     INVENTORY     10  ```
    ```   7     RETURNS       7  ```
    ```    ```
    ```    ```
    ```    ```
    ```    ```
    ```    ```
