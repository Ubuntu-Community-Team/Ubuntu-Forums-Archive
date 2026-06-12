---
title: "Changing location of datadir in MySQL"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by RogerThompson on 2009-01-19
Environment: OS 8.10, MySQL:5.0
I installed this using the package manager, so the file are at the "expected" locations. MySQL will startup with the "vanilla" installation. 

I added a 750GB second disk which is mounted as /media/datadrive1. This is where I want the data in MySQL to be stored.  I went to /etc/mysql and did the following to my.cnf:

# original home
#datadir		= /var/lib/mysql
datadir		= /media/datadrive1/mysql

I copied the contents of /var/lib/mysql into the new datadir.
I made the following change to /etc/apparmor.d/usr.sbin.mysqld:

# Original location of data
#  /var/lib/mysql/ r,
#  /var/lib/mysql/** rwk,
  /media/datadrive1/mysql r,
  /media/datadrive1/mysql/** rwk,

This was done becaause of the note is my.cnf which reads:
#
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#


MySQL will not stay up with the reconfigured my.cnf file.  I get the message from the file /var/log/daemon.log

Jan 19 14:33:59 ThompsonR mysqld_safe[28602]: started
Jan 19 14:33:59 ThompsonR mysqld[28607]: 090119 14:33:59 [Warning] Can't create test file /media/dat
adrive1/mysql/ThompsonR.lower-test
Jan 19 14:33:59 ThompsonR mysqld[28607]: 090119 14:33:59 [Warning] Can't create test file /media/dat
adrive1/mysql/ThompsonR.lower-test
Jan 19 14:33:59 ThompsonR mysqld[28607]: 090119 14:33:59 [ERROR] /usr/sbin/mysqld: Can't find file: 
'./mysql/host.frm' (errno: 13)
Jan 19 14:33:59 ThompsonR mysqld[28607]: 090119 14:33:59 [ERROR] /usr/sbin/mysqld: Can't find file: 
'./mysql/host.frm' (errno: 13)
Jan 19 14:33:59 ThompsonR mysqld[28607]: 090119 14:33:59 [ERROR] Fatal error: Can't open and lock pr
ivilege tables: Can't find file: './mysql/host.frm' (errno: 13)
Jan 19 14:33:59 ThompsonR mysqld_safe[28609]: ended

the errno: 13 translates to: perror 13
OS error code  13:  Permission denied

the owner and group of /media/datadrive/mysql are: mysql, mysql with privs of drwxrwxr-x.

I'm starting the mysqls_safe sudoed to root.

Help.

---

