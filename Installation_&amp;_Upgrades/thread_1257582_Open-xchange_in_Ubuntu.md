---
title: "Open-xchange in Ubuntu"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by bun442000 on 2009-09-04
Currently i'm running Ubuntu, when i try to initialize the open -xchange configdb 
 
database by using this command
 
$ /opt/open-xchange/sbin/initconfigdb --configdb-pass=db_password -a
 
but it will give me this error
 
initializing configdb from scratch...ERROR 1045 (28000) : Access denied for user'root'@'localhost' (using password: NO) 
 
 
 
Even i try to open mysql (currently mysql without password)but it also prompt me to enter password
 
root@xmail:~# mysql -u openxchange -p
Enter password:
ERROR 1045 (28000): Access denied for user 'openxchange'@'localhost' (using password: NO)
 
:confused:

---

### Post by bun442000 on 2009-09-06
Anyone can help ?

---

### Post by Oerb on 2009-10-30
This brings me on the right Way because of the same Problem ;-):
[http://www.open-xchange.com/forum/showthread.php?t=3561](http://www.open-xchange.com/forum/showthread.php?t=3561)

you must set the mysql root password to nothing:

$:mysql --user=root --password=yourPassword

mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('')

:popcorn:

---

