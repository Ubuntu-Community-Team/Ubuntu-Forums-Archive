---
title: "cannot install mysql server"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by dcs.fear on 2009-09-27
hey everyone.
I was having problem with mysql server so i decided to reinstall it. after trying for serveral days. I am not able to install them please help

```

root@xxx:~# apt-get install mysql-server-5.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mysql-server-core-5.0
Suggested packages:
  tinyca mailx
The following NEW packages will be installed:
  mysql-server-5.0 mysql-server-core-5.0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 26.9MB of archives.
After this operation, 88.0MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://mv.archive.ubuntu.com jaunty-updates/main mysql-server-core-5.0 5.1.30really5.0.75-0ubuntu10.2 [3349kB]
Get:2 http://mv.archive.ubuntu.com jaunty-updates/main mysql-server-5.0 5.1.30really5.0.75-0ubuntu10.2 [23.6MB]
Fetched 26.9MB in 3s (7840kB/s)             
Preconfiguring packages ...
Selecting previously deselected package mysql-server-core-5.0.
(Reading database ... 183482 files and directories currently installed.)
Unpacking mysql-server-core-5.0 (from .../mysql-server-core-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb) ...
Selecting previously deselected package mysql-server-5.0.
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb) ...
Processing triggers for man-db ...
Setting up mysql-server-core-5.0 (5.1.30really5.0.75-0ubuntu10.2) ...
Setting up mysql-server-5.0 (5.1.30really5.0.75-0ubuntu10.2) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Reloading AppArmor profiles ...                                       [ OK ] 
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

```
root@xxx:~# apt-get install mysql-server    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mysql-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 57.2kB of archives.
After this operation, 98.3kB of additional disk space will be used.
Get:1 http://mv.archive.ubuntu.com jaunty-updates/main mysql-server 5.1.30really5.0.75-0ubuntu10.2 [57.2kB]
Fetched 57.2kB in 0s (4584kB/s)   
Selecting previously deselected package mysql-server.
(Reading database ... 185866 files and directories currently installed.)
Unpacking mysql-server (from .../mysql-server_5.1.30really5.0.75-0ubuntu10.2_all.deb) ...
 * Stopping MySQL database server mysqld                                                                                                              [ OK ] 
Setting up mysql-server-5.0 (5.1.30really5.0.75-0ubuntu10.2) ...
 * Stopping MySQL database server mysqld                                                                                                              [ OK ] 
 * Reloading AppArmor profiles ...                                                                                                                    [ OK ] 
 * Starting MySQL database server mysqld                                                                                                              [fail] 
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

---

### Post by kranny on 2009-09-27
How about Purging mysql-server..But before that back up your mysql data in /var/lib/mysql

```
sudo cp -r /var/lib/mysql /var/lib/mysql.tmp
```
```
sudo apt-get purge mysql-server
```
```
sudo apt-get install mysql-server
```

Then restore the data that was backed up in the beginning
```
sudo cp -r /var/lib/mysql.b /var/lib/mysql
```
Restart the mysql daemon
```
sudo /etc/init.d/mysql restart
```
and see if it is working

---

### Post by dcs.fear on 2009-09-27
no luck :(

```

root@xxx:~# sudo apt-get purge mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mysql-server is not installed, so not removed
The following packages were automatically installed and are no longer required:
  mysql-server-5.0 mysql-server-core-5.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mysql-server-5.0 (5.1.30really5.0.75-0ubuntu10.2) ...
 * Stopping MySQL database server mysqld                                                                                                              [ OK ] 
 * Reloading AppArmor profiles ...                                                                                                                    [ OK ] 
 * Starting MySQL database server mysqld                                                                                                              [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by sahabcse on 2009-09-27
#sudo apt-get purge mysql-server

#sudo updatedb

#locate mysql

Move the mysql related files to another name.


Then try to reinstall again

---

### Post by kranny on 2009-09-27
Try to Remove it Completely from Synaptic Manager

---

### Post by wojox on 2009-09-27
Run:

```
apt-get -f install
```

Try to force an install of the files that didn't get loaded because of the error.

---

### Post by dcs.fear on 2009-09-28
no luck, the same errors occur :(

---

