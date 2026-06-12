---
title: "CANT Uninstall MYSQL SERVER"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by ncnbnt on 2009-06-10
HEEEELLLPPP....:(:(:(

Im trying to damn uninstall mysql-server cause its misconfigured and with :

```
apt-get remove mysql-server
```it prints :

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  mysql-server psa-api-rpc
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1987kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 30188 files and directories currently installed.)
Removing psa-api-rpc ...
 Trying to start service mysql... done
 Trying to establish test connection...Failed

``````
ERROR while trying to establish test connection
Check the error reason(see log file: /tmp/api-rpc_9.2.1_ubuntu8.04.build92090422.13_installing.090610.15.03.log), fix and try again

Aborting...

dpkg: error processing psa-api-rpc (--remove):
 subprocess post-removal script returned error exit status 1
Removing mysql-server ...
Errors were encountered while processing:
 psa-api-rpc
E: Sub-process /usr/bin/dpkg returned an error code (1)
```I checked the /tmp/api-rpc_9.2.1_ubuntu8.04.build92090422.13_installing.090610.15.03.log and:

```
START api-rpc-9.2.1-ubuntu8.04.build92090422.13 installing (deb action: remove) AT Wed Jun 10 15:03:25 GMT 2009
dpkg action:
 Trying to start service mysql... /usr/sbin/mysqld (pid 7780) is running...
done
 Trying to establish test connection... ERROR 1045 (28000): Access denied for user 'admin'@'localhost' (using password: YES)
ERROR 1045 (28000): Access denied for user 'admin'@'localhost' (using password: YES)
ERROR 1045 (28000): Access denied for user 'admin'@'localhost' (using password: YES)
ERROR 1045 (28000): Access denied for user 'admin'@'localhost' (using password: YES)
ERROR 1045 (28000): Access denied for user 'admin'@'localhost' (using password: YES)
ERROR 1045 (28000): Access denied for user 'admin'@'localhost' (using password: YES)
ERROR 1045 (28000): Access denied for user 'admin'@'localhost' (using password: YES)
ERROR 1045 (28000): Access denied for user 'admin'@'localhost' (using password: YES)
ERROR 1045 (28000): Access denied for user 'admin'@'localhost' (using password: YES)
```
WHAT is going on...OMG.... . It destroys my server....I installed first the PLESK Panel and then it happened the problem.I removed the plesk and now only this DAMN  **psa-api-rpc** CANT BE removed.

PLEASEEEEE..:(:(:(:(:(
Thanks

---

### Post by ncnbnt on 2009-06-10
anyone pleasssee

---

### Post by dstew on 2009-06-10
Try **sudo** apt-get remove mysql-server

---

### Post by ncnbnt on 2009-06-10
Same thing.The problem is something in mysql user or something like that.

Thanks anyway

---

### Post by cariboo on 2009-06-10
Try:

```
sudo apt-get purge mysql-server-5.0
```

mysql-server is just a meta-package.

---

### Post by ncnbnt on 2009-06-10
Thanks but same damn thing.

It says it will remove them but  prints 
Trying to start service mysql... done
 Trying to establish test connection...Failed

---

### Post by ncnbnt on 2009-06-10
The Problem iS not mysql BUT 



```
Errors were encountered while processing:
 psa-api-rpc
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by mdmarmer on 2009-06-10
The post above is correct

You may need some hints on how to fix the problem

[http://sidux.com/index.php?module=pnWikka&tag=FixAPT](http://sidux.com/index.php?module=pnWikka&tag=FixAPT)

I should probably try to find an Ubuntu reference -- if you use the sidux wiki, don't forget to sudo ;-)

Mike

---

### Post by ncnbnt on 2009-06-10
thanks a lot mate but problem still exist..

How to damn delete the user: admin from the database?

---

### Post by woozly on 2009-06-10
Hi,
it looks like mysql will check if you have privs to delete the databases installed on the system.. try to find a proof..
 
start mysql without any rights
 
#usr/bin/mysqld_safe --skip-grant-tables
#apt-get remove mysql.....
 
or ...
try to reset passwd to '' 
[http://www.debian-administration.org/articles/442](http://www.debian-administration.org/articles/442)
 
Otherwise you can remove installed files by hand checking. list of installed files from deb pakage....
 
#dpkg -L mysql-server 
#dpkg -L mysql-server-5.0
 
[SIZE=1]woo[/SIZE]

---

### Post by woozly on 2009-06-10
[SIZE=1]...[/SIZE]

---

### Post by woozly on 2009-06-10
found somewhere .....
try #dpkg-reconfigure mysql-server-5.0
 
woo

---

### Post by ncnbnt on 2009-06-11
Yihhhaaaaaa..

I dont know how my friends ,but its ok now.


1000000 Thanks:p:p:p:p

---

### Post by FewG on 2010-03-21
I have the same problem, How can I solve it?

---

