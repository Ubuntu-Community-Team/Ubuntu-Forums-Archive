---
title: "Installing MySql5"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by bohn002 on 2009-02-23
Ok, I am totally confused. I wanted to reinstall a local server installation. So I purged my Apache2, Php and Mysql. i went to install my mysql after the previous 2 went ok (php and apache), and just having trouble after googling this thing to death.

I am trying to do 
sudo apt-get install mysql-server-5.0
and this is what I get: 

```
nbohn@nbohn-desktop:~$ sudo apt-get install mysql-server-5.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server-5.0 is already the newest version.
mysql-server-5.0 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mysql-server-5.0 (5.0.67-0ubuntu6) ...
 * Stopping MySQL database server mysqld                                           [ OK ] 
Reloading AppArmor profiles : done.
 * Starting MySQL database server mysqld                                           [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have purged, installed mysql-server removed sql commons. and so much more. So any additional help would be great to get this working again.

---

### Post by khelben1979 on 2009-02-23
What happens if you use the graphical installer [Synaptic]("http://en.wikipedia.org/wiki/Synaptic_Package_Manager") for this instead?

---

### Post by bohn002 on 2009-02-23
ok well found this and this seems to work???
```
sudo apt-get remove apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql
```

and then 
```
sudo apt-get install apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql
```

---

