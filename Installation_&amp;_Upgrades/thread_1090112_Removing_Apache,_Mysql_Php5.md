---
title: "Removing Apache, Mysql Php5"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by bob092588 on 2009-03-07
hello i have tried every thing to remove this the following commnads are what i have used so far 

sudo apt-get remove apache2
sudo apt-get autoremove 
sudo aptitude remove apache2
sudo aptitude purge apache2 

i have used these command of all three of them can any one help 

thank you 

bob

---

### Post by utnubuuser on 2009-03-07
sudo aptitude remove apache2 --purge

---

### Post by bob092588 on 2009-03-07
> **utnubuuser said:**
> sudo aptitude remove apache2 --purge

it did not work :( when i went to install mysql-server again it said it would need to take up 90 kb mysql need more then that :(
```
bob@sensai-desktop:~$ sudo aptitude remove mysql-server  --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

bob@sensai-desktop:~$ sudo apt-get install mysql_server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mysql_server
bob@sensai-desktop:~$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mysql-server
0 upgraded, 1 newly installed, 0 to remove and 14 not upgraded.
Need to get 0B/54.9kB of archives.
After this operation, 90.1kB of additional disk space will be used.
Selecting previously deselected package mysql-server.
(Reading database ... 109852 files and directories currently installed.)
Unpacking mysql-server (from .../mysql-server_5.0.67-0ubuntu6_all.deb) ...
 * Stopping MySQL database server mysqld                                                                                                                                    [ OK ] 
Setting up mysql-server (5.0.67-0ubuntu6) ...
bob@sensai-desktop:~$ 
```

---

