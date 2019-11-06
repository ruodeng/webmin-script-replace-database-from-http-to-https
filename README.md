# webmin-script-replace-database-from-http-to-https
A custom webmin script which can replace http to https for mysql database.

#DUMP to a file

`mysqldump  $user > /root/$user.sql;` 

#copy origin file for backup

`cp /root/$user.sql /root/origin/$user.sql;` 

#In this condition, we using wordpress, and it with lots of contents.  like a.dengruo.com b.dengruo.com, I want replace all into https

`sed  -i -r -e    's/http\:\/\/([a-z]+)\.dengruo\.com/https\:\/\/\1\.dengruo\.com/g'  /root/$user.sql;`

#import back to mysql

`mysql   $user <  /root/$user.sql;` 
