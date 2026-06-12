---
title: "problem with installing mysql-server"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by bagrx on 2009-06-09
I have problem with installing mysql-server 
I've looked at similar problems but not been able to find a solution. 

# aptitude install mysql-server-5.0
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following NEW packages will be installed:
  mysql-server-5.0
0 packages upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/24.0MB of archives. After unpacking 81.4MB will be used.
Writing extended state information... Done
Preconfiguring packages ...
(Reading database ... 235008 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_amd64.deb) ...
Aborting downgrade from (at least) 5.1 to 5.0.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done

---

### Post by Partyboi2 on 2009-06-10
Hi, open a terminal and try moving/var/lib/mysql folder out of the way
```
sudo mv /var/lib/mysql /var/lib/mysql.old
```
then
```
sudo aptitude install mysql-server-5.0
```

[http://senseq-techtips.blogspot.com/2009/03/mysql-51-downgrade-to-mysql-50-on.html](http://senseq-techtips.blogspot.com/2009/03/mysql-51-downgrade-to-mysql-50-on.html)

---

### Post by bagrx on 2009-06-10
Partyboi2 thx for solution 

```

mv /var/lib/mysql /var/lib/mysql.old
aptitude install mysql-server-5.0

```after installation there was problem /var/lib/dpkg/info/mysql-server-5.0.postinst: line 144: /etc/mysql/conf.d/old_passwords.cnf: No such file or directory                            
 
[ solution]("http://ubuntuforums.org/archive/index.php/t-891109.html")
```

mkdir /etc/mysql/conf.d
chown -R mysql:mysql /var/lib/mysql/*
dpkg --configure -a  
```

now mysql works, thx

---

