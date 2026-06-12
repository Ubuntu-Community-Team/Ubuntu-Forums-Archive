---
title: "[SOLVED] Mysql not starting up during bootup???"
date: 2008-11-08
forum: General Help
---

### Post by reality1011 on 2008-11-08
For some odd reason I can't get mysql to start during bootup.  
I am able to manually start the mysql demon but this defeats the purpose of having it in rc.d...

Fyi... 
```
cappetta@Linux-Box:/var/log/mysql$ lsb_release -dc
Description:    Ubuntu 7.10
Codename:       gutsy

```


I have also tried 
```
update-rc.d mysql remove 

``` 

and then 

```
update-rc.d mysql defaults

```


I see the following in the system log...

> Nov  8 08:23:28 localhost /etc/init.d/mysql[6282]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Nov  8 08:23:28 localhost /etc/init.d/mysql[6282]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Nov  8 08:23:28 localhost /etc/init.d/mysql[6282]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Nov  8 08:23:28 localhost /etc/init.d/mysql[6282]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Nov  8 08:23:28 localhost /etc/init.d/mysql[6282]:



Any troubleshooting advice is appreciated.  I am not sure why this is happening but the mysql demon is located in all levels of rc.d


```

cappetta@Linux-Box:/var/log/mysql$ ll /etc/rc*/*mysql
lrwxrwxrwx 1 root root 15 2008-11-08 08:28 /etc/rc0.d/K20mysql -> ../init.d/mysql
lrwxrwxrwx 1 root root 15 2008-11-08 08:28 /etc/rc1.d/K20mysql -> ../init.d/mysql
lrwxrwxrwx 1 root root 15 2008-11-08 08:28 /etc/rc2.d/S20mysql -> ../init.d/mysql
lrwxrwxrwx 1 root root 15 2008-11-08 08:28 /etc/rc3.d/S20mysql -> ../init.d/mysql
lrwxrwxrwx 1 root root 15 2008-11-08 08:28 /etc/rc4.d/S20mysql -> ../init.d/mysql
lrwxrwxrwx 1 root root 15 2008-11-08 08:28 /etc/rc5.d/S20mysql -> ../init.d/mysql
lrwxrwxrwx 1 root root 15 2008-11-08 08:28 /etc/rc6.d/K20mysql -> ../init.d/mysql
cappetta@Linux-Box:/var/log/mysql$


```

---

### Post by reality1011 on 2008-11-09
Bump to the top...

---

### Post by reality1011 on 2008-11-09
An answer isnt needed but trouble shooting would definitely help....

---

### Post by reality1011 on 2008-11-10
read me-- please

---

### Post by reality1011 on 2008-11-11
wow...

---

### Post by -Zeus- on 2008-11-11
what happens if you run ```
sudo /etc/init.d/mysql start
```

---

### Post by reality1011 on 2008-11-12
It works as expected

> 
cappetta@Linux-Box:/var/www/products$ sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                                                                                               [ OK ]
cappetta@Linux-Box:/var/www/products$


---

### Post by reality1011 on 2008-11-13
ping?

---

### Post by zeke9999 on 2008-11-14
I have the same problem and this was working in 8.04 (might still work in but haven't checked) and 8.10 until recently. It seems to have to do with networking not being ready when mysql starts looking for the bind-address. 

This might be a solution: [http://ge.ubuntuforums.com/showthread.php?t=678581](http://ge.ubuntuforums.com/showthread.php?t=678581). But there's some problem with it in intrepid right now.

---

### Post by reality1011 on 2008-11-25
So after a week of on and off testing, mysql is still not coming up on boot...  

does anyone know how I can trace my startup?

---

### Post by unutbu on 2008-11-25
I don't know how to fix your problem, but would you please post the output of 
```

dpkg --get-selections | awk '/mysql/{print $1}' | xargs apt-cache policy
```
This will show us what mysql packages you have installed.

---

### Post by reality1011 on 2008-11-25
Here you go:

> 
cappetta@Linux-Box:~$ dpkg --get-selections | awk '/mysql/{print $1}' | xargs apt-cache policy
libapache2-mod-auth-mysql:
  Installed: 4.3.9-4
  Candidate: 4.3.9-4
  Version table:
 *** 4.3.9-4 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
        100 /var/lib/dpkg/status
libdbd-mysql-perl:
  Installed: 4.004-2
  Candidate: 4.004-2
  Version table:
 *** 4.004-2 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
        100 /var/lib/dpkg/status
libmysqlclient15off:
  Installed: 5.0.45-1ubuntu3.3
  Candidate: 5.0.45-1ubuntu3.4
  Version table:
     5.0.45-1ubuntu3.4 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
 *** 5.0.45-1ubuntu3.3 0
        100 /var/lib/dpkg/status
     5.0.45-1ubuntu3 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
mysql-client:
  Installed: 5.0.45-1ubuntu3.3
  Candidate: 5.0.45-1ubuntu3.4
  Version table:
     5.0.45-1ubuntu3.4 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
 *** 5.0.45-1ubuntu3.3 0
        100 /var/lib/dpkg/status
     5.0.45-1ubuntu3 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
mysql-client-5.0:
  Installed: 5.0.45-1ubuntu3.3
  Candidate: 5.0.45-1ubuntu3.4
  Version table:
     5.0.45-1ubuntu3.4 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
 *** 5.0.45-1ubuntu3.3 0
        100 /var/lib/dpkg/status
     5.0.45-1ubuntu3 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
mysql-common:
  Installed: 5.0.45-1ubuntu3.3
  Candidate: 5.0.45-1ubuntu3.4
  Version table:
     5.0.45-1ubuntu3.4 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
 *** 5.0.45-1ubuntu3.3 0
        100 /var/lib/dpkg/status
     5.0.45-1ubuntu3 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
mysql-server:
  Installed: 5.0.45-1ubuntu3.3
  Candidate: 5.0.45-1ubuntu3.4
  Version table:
     5.0.45-1ubuntu3.4 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
 *** 5.0.45-1ubuntu3.3 0
        100 /var/lib/dpkg/status
     5.0.45-1ubuntu3 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
mysql-server-5.0:
  Installed: 5.0.45-1ubuntu3.3
  Candidate: 5.0.45-1ubuntu3.4
  Version table:
     5.0.45-1ubuntu3.4 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
 *** 5.0.45-1ubuntu3.3 0
        100 /var/lib/dpkg/status
     5.0.45-1ubuntu3 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
php5-mysql:
  Installed: 5.2.3-1ubuntu6.4
  Candidate: 5.2.3-1ubuntu6.4
  Version table:
 *** 5.2.3-1ubuntu6.4 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
        100 /var/lib/dpkg/status
     5.2.3-1ubuntu6 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
python-mysqldb:
  Installed: 1.2.2-3ubuntu1
  Candidate: 1.2.2-3ubuntu1
  Version table:
 *** 1.2.2-3ubuntu1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
        100 /var/lib/dpkg/status
cappetta@Linux-Box:~$


---

### Post by unutbu on 2008-11-25
Please post (or attach) your /etc/mysql/my.cnf
I'll ediff it against mine...

You might also want to run this command:
```

sudo apt-get purge --simulate mysql-common
```
This will simulate the removal of the mysql-common package and all packages that depend on it.
It will list all the packages that would be removed.
If purging and then reinstalling that list is acceptable to you, then maybe doing so would be the easiest way to fix this problem. (To purge for real, remove the --simulate flag from the command above.)

Note that it is important to purge rather than simply remove, because only purging deletes configuration files.

---

### Post by reality1011 on 2008-11-25
Here is the my.cnf file; I will review the purge output and see if its feesible to preform.  I will probably have to look into backing up the databases so if you have anything handy that would be appreciated.. I am sure google will have something.


> 
cappetta@Linux-Box:~$ cat  /etc/mysql/my.cnf
#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.
#
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# [http://dev.mysql.com/doc/mysql/en/server-system-variables.html](http://dev.mysql.com/doc/mysql/en/server-system-variables.html)

# This will be passed to all mysql clients
# It has been reported that passwords should be enclosed with ticks/quotes
# escpecially if they contain "#" chars...
# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
[client]
port            = 3306
socket          = /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket          = /var/run/mysqld/mysqld.sock
nice            = 0

[mysqld]
#
# * Basic Settings
#
user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
language        = /usr/share/mysql/english

skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
#bind-address           =192.168.0.134
bind-address            =127.0.0.1

#
# * Fine Tuning
#
key_buffer              = 16M
max_allowed_packet      = 16M
thread_stack            = 128K
thread_cache_size       = 8
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit       = 1M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
log             = /var/log/mysql/mysql.log
#
# Error logging goes to syslog. This is a Debian improvement :)
#
# Here you can see queries with especially long duration
#log_slow_queries       = /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id              = 1
log_bin                 = /var/log/mysql/mysql-bin.log
# WARNING: Using expire_logs_days without bin_log crashes the server! See README.Debian!
expire_logs_days        = 10
max_binlog_size         = 100M
#binlog_do_db           = include_database_name
#binlog_ignore_db       = include_database_name
#
# * BerkeleyDB
#
# Using BerkeleyDB is now discouraged as its support will cease in 5.1.12.
skip-bdb
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
# You might want to disable InnoDB to shrink the mysqld process by circa 100MB.
#skip-innodb
#
# * Security Features
#
# Read the manual, too, if you want chroot!
# chroot = /var/lib/mysql/
#
# For generating SSL certificates I recommend the OpenSSL GUI "tinyca".
#
# ssl-ca=/etc/mysql/cacert.pem
# ssl-cert=/etc/mysql/server-cert.pem
# ssl-key=/etc/mysql/server-key.pem



[mysqldump]
quick
quote-names
max_allowed_packet      = 16M

[mysql]
#no-auto-rehash # faster start of mysql but no tab completition

[isamchk]
key_buffer              = 16M

#
# * NDB Cluster
#
# See /usr/share/doc/mysql-server-*/README.Debian for more information.
#
# The following configuration is read by the NDB Data Nodes (ndbd processes)
# not from the NDB Management Nodes (ndb_mgmd processes).
#
# [MYSQL_CLUSTER]
# ndb-connectstring=127.0.0.1


#
# * IMPORTANT: Additional settings that can override those from this file!
#
!includedir /etc/mysql/conf.d/

cappetta@Linux-Box:~$


---

### Post by unutbu on 2008-11-25
[list=1]
[*]This might work, but it's a longshot:
I notice in your error messages

```
Nov 8 08:23:28 localhost /etc/init.d/mysql[6282]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
```

And I notice in your /etc/mysql/my.cnf
```

bind-address =127.0.0.1
```

Could it be that mysql doesn't know that 127.0.0.1 is the same thing as localhost?

My /etc/mysql/my.conf happens to say
```

bind-address		= localhost
```

You might want to try that. A longshot, but at least it is easy to try.
[*]If that doesn't work, and you would like to continue trying to fix this without purging, then the only other thing I can think of is that this might be a permissions/ownership problem. In that case, please post
```

ls -l $(which mysql)
ls -l $(which mysqld)
ls -la /etc/mysql
ls -la /var/lib/mysql
ls -la /var/run/mysqld/
cat /etc/hosts

```
[*]If you would like to try purging, then to backup your databases,
```

sudo rsync -a /var/lib/mysql/DATABASE/ /path/to/backup/location
```

The slash after DATABASE is important; without the slash DATABASE gets copied to 
/path/to/backup/location/var/lib/mysql/DATABASE instead of /path/to/backup/location/DATABASE.

Once you reinstall mysqld, try to get it to start up automatically at boot before adding your database back. There are instructions here on how to set up the mysql root password:
[https://help.ubuntu.com/community/ApacheMySQLPHP#Set%20mysql%20root%20password](https://help.ubuntu.com/community/ApacheMySQLPHP#Set%20mysql%20root%20password)

Once you get that working, then 

```
sudo rsync -a /path/to/backup/location/DATABASE/ /var/lib/mysql/DATABASE/ 
```

will restore your data.
[/list]

---

### Post by reality1011 on 2008-11-25
very nice... I am also looking at the runlevel scripts.  I was just reading up on something that said :

> ... No scripts are run when entering runlevel S
 .........

When entering a runlevel, all the kill or stop scripts are run first before processing the start scripts. On bootup, things are a bit different. Because we have not come from another runlevel, all the kill or stop scripts are skipped. There is no need in stopping services that cannot be running in the first place. It should also be noted that a kill or stop script and a start script can exist for the same service in the same runlevel. This would cause the service to be restarted upon entering that runlevel.





---

### Post by reality1011 on 2008-11-25
Ok...  RESOLVED !


Man this was a fricken hassel.... It was a combination of a couple of different things...

First,  I did modify my /etc/hosts file and purposely commented out localhost... when you saw that there was problem with resolving localhost, I realized my /etc/host file was modified when I was configuring/troubleshooting my virtual hosting... which is when this problem first started appearing...

On top of that, I had to create a start_mysql script and install into the runlevels, using: 

```

cappetta@Linux-Box:~$ cat /etc/init.d/start_mysql
#! /bin/sh
# Reload the Mysql server when an interface comes up, to allow it to start
# listening on new addresses.
log="/tmp/mysql_network.log"
set -e
echo "DATE TIME STARTED: `date`" >> $log

# Is /usr mounted?
if [ ! -e /usr/sbin/mysqld ]; then
        echo " /usr/sbin/mysqld not exist "  >> $log
#       exit 0
fi

/etc/init.d/mysql start  >> log
echo " " >> $log
echo " searching for process " >> $log
echo " `ps -eaf | grep -i mysql`" >> $log
exit 0


cappetta@Linux-Box:~$ sudo update-rc.d start_mysql defaults
 Adding system startup for /etc/init.d/start_mysql ...
   /etc/rc0.d/K20start_mysql -> ../init.d/start_mysql
   /etc/rc1.d/K20start_mysql -> ../init.d/start_mysql
   /etc/rc6.d/K20start_mysql -> ../init.d/start_mysql
   /etc/rc2.d/S20start_mysql -> ../init.d/start_mysql
   /etc/rc3.d/S20start_mysql -> ../init.d/start_mysql
   /etc/rc4.d/S20start_mysql -> ../init.d/start_mysql
   /etc/rc5.d/S20start_mysql -> ../init.d/start_mysql


```


Thank you for all your help... Im glad this beast is finally behind me but I do wonder, at the same time, why mysqld is not loading on normal bootup.

---

