---
title: "Help with mysql error"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by satish_j on 2009-03-20
Iam not able to connect to mysql server through php pages.I get error as 
```

'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) in /usr/local/apache2/htdocs/openDB.php on line 4
Error connecting to mysql'

```
However,when i can connect to mysql server through command prompt without any issue.
In my.cnf,i have foll setting:
```

#socket		= /var/run/mysqld/mysqld.sock
socket		= /tmp/mysql.sock

```
I have commented original setting of 'va/run/mysqld/mysqld.sock' since the file is getting created at '/tmp/mysql.sock'
bind-address is set to 127.0.0.1
Desperately seeking solution...Any suggestions...

---

### Post by dusan.saiko on 2009-03-21
Are you connecting from PHP through socket or trying to access server using tcp/ip ?

If you can connect to mysql on command prompt and you are sure you know the right credentials, then you probably have only a problem creating mysql connection from pgp. First make sure again the username / password is correct and then see

[http://au2.php.net/function.mysql-connect](http://au2.php.net/function.mysql-connect)

in case you want to use tcp
[http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html](http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html)

---

### Post by satish_j on 2009-03-21
Iam trying to connect to mysql server through PHP pages and i suppose it uses socket for this.(iam a newbie to mysql) since the err specifies something_connection to socket_
Is there setting that needs to be done in php.ini so as to access mysql server through php pages??
I dont want to re-install all the stuffs again since i think that is not a technical solution to my prob..
Awaiting for some other possible solutions...

---

### Post by satish_j on 2009-03-22
Still struggling with the error..
Can anyone provide a working php.ini and my.cnf from a Linux machine???
Thanks..

---

### Post by jadymitchell on 2009-03-24
Same problem here; I think there were some recent updates to php5 and apache that may have triggered the problem.  Have there been any developments on a fix?

---

### Post by satish_j on 2009-03-25
My problem is resolved..it was a case of missing php.ini in /usr/local/lib folder.
I had compiled PHP manually from source.So,the php.ini file was missing from above path.
Copied php-ini.redist to above path and renamed it to php.ini-->restarted apache and prob solved..
I think this forum is not the right place to post software issues..It is best suited to solve Linux OS issues.

---

