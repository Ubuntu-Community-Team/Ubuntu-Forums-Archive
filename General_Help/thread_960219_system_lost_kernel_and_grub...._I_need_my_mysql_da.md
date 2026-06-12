---
title: "system lost kernel and grub.... I need my mysql databases so bad.."
date: 2008-10-27
forum: General Help
---

### Post by bronkeydain on 2008-10-27
Hello fellow ubuntu-ers,

Excuse my ignorance as I am a n00b and I have already posted this as a MYSQL problem but I am getting no assistance, and it is not a mysql only problem:

My ext3 filesystem just got corrupted one day to another. I have managed to recover the file system and the files (using testdisk and e2sfck) but have also deleted the MBR: My system won't boot, I found it is missing /boot with grub and the kernel.

ALL I WANT IS MY MYSQL DATABASES! (Or really just my 1 vTiger database).

After having made my fie system readable again I have made a clone of the disk using dd. Then I have tried to copy /var/lib/mysql, then /var, then /, whatever I do I run from one problem to another. 

My question is: Which way to go to fix this problem? Should I concentrate on getting the HD to boot again, or to get Mysql working on a new machine by copying the files? Please could anyone give some guidance, I know my data is on the drive and I am sure this problem is fixable. I myself have already tried for 2 weeks with no joy.

The original system uses ubuntu desktop 7.10 and Mysql 5.0.45

Anyone that can help pleeeeeeeeeeeeezzzz?

---

### Post by bronkeydain on 2008-10-27
At the moment I am rebuilding another system as again I am reading that copying /var/lib/mysql is the way to recover mysql databases....

---

### Post by geirha on 2008-10-27
Ok try this. Boot the ubuntu 7.10 CD, install mysql in the live session ```
sudo aptitude install mysql-server mysql-client
``` 

The installation will automatically start mysql-server, so stop it again with ```
sudo /etc/init.d/mysql stop
``` 

Copy the contents of /var/lib/mysql on your broken ext3 filesystem to the live session's /var/lib/mysql, then start mysql again ```
sudo /etc/init.d/mysql start
```

Try connecting to your database and see if it looks ok, if it does, do a database dump 
```

sudo mysqldump --all-databases > mysql.sql
# or just that one database
sudo mysqldump vTiger >vTiger.sql

```

I believe you should now be able to import your database in a new system.

Installing a kernal again and getting grub to boot might be an option too, but if /boot has disappeared, there might be other things that have disappeared as well, which may make it hard to fix. Taking a backup of your mysql database, then reinstall sounds like the easiest option to me.

---

### Post by bronkeydain on 2008-10-27
Ahhh finally some assistance. thank you so much geirha!
I will try your recommendations ASAP and report back here, it sounds very promising :)

---

### Post by bronkeydain on 2008-10-27
I have tried the above but I am running into an error.

I have mounted my old disk as /media/hdb:
```
sudo mount /dev/hdb1 hdb/
```

Stopped the database:
```
/etc/init.d/mysql stop
```

Copied the files over:
```
sudo cp -Rf /media/hdb/var/lib/mysql/* /var/lib/mysql
```

Started the database:
```
 sudo /etc/init.d/mysql start
```

But then run into this:
```
 * Starting MySQL database server mysqld                                                                                                              [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
ubuntu@ubuntu:/media/hdb$ ERROR 1045 (28000): Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)
```

It did copy some databases, but not vtigercrm504... the one that matters, eek!
```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema | 
| egroupware         | 
| ghtest             | 
| mysql              | 
| testdb             | 
| ttx                | 
+--------------------+
```

Got another lifeline?

---

### Post by geirha on 2008-10-27
Could be a permission issue. All tables should be readable and writable to the mysql user and mysql group.

Try preserving permissions when copying.
```
sudo mv /var/lib/mysql /var/lib/mysql.old
sudo cp -a /media/hdb/var/lib/mysql/ /var/lib/mysql

```

---

### Post by bronkeydain on 2008-10-27
Thanks again geirha, I really appreciate your help.

I have copied /var/lib/mysql, preserving permissions. I keep getting this authetication error now when I start mysql.

```
ubuntu@ubuntu:/media/hdb$ sudo mv /var/lib/mysql /var/lib/mysql.old
ubuntu@ubuntu:/media/hdb$ sudo cp -a /media/hdb/var/lib/mysql/ /var/lib/mysql
ubuntu@ubuntu:/media/hdb$ sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                                                                                              [ OK ] 
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'


```

---

### Post by bronkeydain on 2008-10-27
And I have tried:

```
ubuntu@ubuntu:/var/lib/mysql$ sudo chown -R mysql:mysql *
```
But no joy... I am off to bed for now... cya tomorrow :D

---

### Post by geirha on 2008-10-27
Ok, we are overwriting mysql's user-database, and that is probably why it can't connect as that mysql-user when it's starting the server. So try copying just the databases over. That is, all directories in /media/hdb/var/lib/mysql/ except /media/hdb/var/lib/mysql/mysql/

We don't need the user and host tables since we'll do the dump with mysql's root user.

---

### Post by bronkeydain on 2008-10-28
That makes sense. I will try a bit later and report back. Thanks again for the suggestions..

---

### Post by bronkeydain on 2008-10-28
I copied all files from /media/hdb/var/lib/mysql to /var/lib/mysql, excluding /media/hdb/var/lib/mysql/mysql.

Then when I tried to start mysql:

```
ubuntu@ubuntu:/var/lib/mysql$ sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                                                                                              [fail] 
ubuntu@ubuntu:/var/lib/mysql$ sudo /etc/init.d/mysql status
 * MySQL is stopped.

```

I will try once more to make sure I have not made a mistake somewhere.

---

### Post by geirha on 2008-10-28
Check /var/log/daemon.log, /var/log/mysql.err and /var/log/mysql.log to see if it has logged any useful error messages

```
tail /var/log/{daemon.log,mysql.{err,log}}
```

---

### Post by bronkeydain on 2008-10-28
Hey Geirha, do you never sleep?

As soon as I hit restart I realized I should have looked at the logs.
Anyway I have tried again. This time it does start mysql, but when I do a query it gives me an error.

SQL Query
```
mysql> use egroupware
Database changed
mysql> show tables;
ERROR 1018 (HY000): Can't read dir of './egroupware/' (errno: 13)
mysql> quit
Bye

```

Log:
```
ubuntu@ubuntu:/media/hdb/var/lib/mysql.new$ tail /var/log/{daemon.log,mysql.{err,log}}
==> /var/log/daemon.log <==
Oct 28 10:05:57 ubuntu mysqld_safe[9287]: ended
Oct 28 10:07:34 ubuntu mysqld_safe[9406]: started
Oct 28 10:07:34 ubuntu mysqld[9409]: 081028 10:07:34  InnoDB: Started; log sequence number 0 16993760
Oct 28 10:07:34 ubuntu mysqld[9409]: 081028 10:07:34 [Note] /usr/sbin/mysqld: ready for connections.
Oct 28 10:07:34 ubuntu mysqld[9409]: Version: '5.0.45-Debian_1ubuntu3-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Debian etch distribution
Oct 28 10:07:35 ubuntu /etc/mysql/debian-start[9445]: Upgrading MySQL tables if necessary.
Oct 28 10:07:35 ubuntu /etc/mysql/debian-start[9450]: Looking for 'mysql' in: /cow/usr/bin/mysql
Oct 28 10:07:35 ubuntu /etc/mysql/debian-start[9450]: FATAL ERROR: Can't find '/cow/usr/bin/mysql'
Oct 28 10:07:35 ubuntu /etc/mysql/debian-start[9451]: Checking for insecure root accounts.
Oct 28 10:07:35 ubuntu /etc/mysql/debian-start[9455]: Checking for crashed MySQL tables.

```

---

### Post by geirha on 2008-10-28
Not sure about that fatal error in the logs, but the errno 13 sounds like you need chown and/or chmod the database dir so it is owned by the mysql user and mysql group, and writable to mysql

---

### Post by bronkeydain on 2008-10-28
DOH I think I forgot to copy preserving permissions. I have to drop someone off at the airport. Back in a while and I will give it another go. Thanks again Geirha

---

### Post by bronkeydain on 2008-10-28
I have tried to copy again using -a to preserve permissions and I got the same error. Then I did chown mysql:mysql and chmod 777 on all files in the /var/lib/mysql folder and now everything seems to work fine. I can connect to my egroupware database and all data seem to be there.

However my vtigercrm504 database is just not there :confused:
Every single file on that machine seems to be there but not the single only one that matters. 
I suppose that is it or do you have another rabbit to pull out of your hat Geirha? 

This whole story is incredible because I did daily tar backups and mysqldumps to a USB HD, keeping 5 generations of each and checking the log file twice a week. When my filesystem got scrambled my backups were unreadable as well, it seemed that the dumps were cut in half. 

If I have lost my database then that is a little disaster for me but at least now I know and I can focus on rebuilding it. I have learnt a lot from you Geirha, hope I can return the favor one day.

---

### Post by geirha on 2008-10-28
The backups you did to the external harddrive got corrupted as well as the root filesystem? That sounds very odd. What filesystem do you have on the external drive, and what's the size of the backups and what size should they be?

---

### Post by bronkeydain on 2008-10-28
I think that question was spot on.

The reason I said my backups were unreadable is because I was having the following problem trying to import the backup sqldumps:
(I had posted this on another thread I will try and sum it up below [http://ubuntuforums.org/showthread.php?t=953538]("http://ubuntuforums.org/showthread.php?t=953538")

```
- Then I type: mysql -u root -p vtigercrm504 < vtigercrm504.09.10.2008.sqlbackup 
> When I enter the SQL password, then I get this error: 
ERROR 1136 (21S01) at line 1323: Column count doesn't match value count at row 9 
```
I was getting the exact same error for my egroupware database (well, different line number and row number).
Indytim suggested to open the sqldump file, skip to line 1323 in this case and check to see if it is missing some data. I jumped to that line, it was a huge line making it impossible to check if fields were missing. But it was also the last line in the dump, that is why I thought it was cut off half way.

Now I looked at the orginal dump again and it actually did complete (the last line says -- Dump completed on 2008.....etc). I can actually see my data in it!! I will try and import this dump into a live session and report back.

---

### Post by bronkeydain on 2008-10-28
I am getting another error (/me mumbles something about frustrating and I love my mac).

```
ubuntu@ubuntu:~$ sudo mysql -u root -p vtigercrm504 < /home/ubuntu/Desktop/vtigercrm504.09.10.2008.sqlbackup 
Enter password: 
ERROR 1064 (42000) at line 607: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'Emails','Save','','2008-08-27 16:25:18'),(3408,4,'Leads','index','','2008-08-27 ' at line 1
```

This is supposed to be the same database that I tried importing on the example above.

---

### Post by geirha on 2008-10-28
Hm, how big is the version difference between the mysql you dumped it from and the one you're trying to import it to now?

```
head vtigercrm504.09.10.2008.sqlbackup
mysql --version
```

The error messages from mysql are cryptic as always :) First it says at line 607, then at the end it says it's at line 1. Googling the error give lots of hits, but not much to go on. 

This one is interesting however: [http://drupal.org/node/144444](http://drupal.org/node/144444)
Check the bottom post, redirecting the script with the shell didn't work, but sourcing it from mysql did ...

---

### Post by bronkeydain on 2008-10-28
Same version. Interesting link indeed. I will give this a shot tomorrow as I am ready for bed. Thanks Geirha my friend, your help is so much apreciated.

```
ubuntu@ubuntu:/media/disk$ head vtigercrm504.09.10.2008.sqlbackup
-- MySQL dump 10.11
--
-- Host: localhost    Database: vtigercrm504
-- ------------------------------------------------------
-- Server version       5.0.45-Debian_1ubuntu3.3-log

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8 */;
ubuntu@ubuntu:/media/disk$ mysql --version
mysql  Ver 14.12 Distrib 5.0.45, for pc-linux-gnu (i486) using readline 5.2
```

---

### Post by bronkeydain on 2008-10-29
I have started clean again with Live session:

```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema | 
| mysql              | 
+--------------------+
2 rows in set (0.00 sec)

mysql> create database vtigercrm504;
Query OK, 1 row affected (0.00 sec)

mysql> use vtigercrm504;
Database changed

mysql> source ./vtigercrm504.09.10.2008.sqlbackup
```

This gives me 2 errors I can see on the console, I am not sure how to read /var/log/mysql/mysql-bin.000011 which seem to be the most recent log.

```
ERROR 1136 (21S01): Column count doesn't match value count at row 180
ERROR 1100 (HY000): Table 'vtiger_industry' was not locked with LOCK TABLES
Query OK, 0 rows affected (0.00 sec)
```

and 

```
ERROR 1103 (42000): Incorrect table name 'vtiger_invoiceship (
```
  '
It has done more than other times, but still ](*,)

---

### Post by bronkeydain on 2008-10-29
This is from the daemon.log, mysql.err and mysql.log:

Oct 29 08:21:11 ubuntu mysqld_safe[9255]: PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
Oct 29 08:21:11 ubuntu mysqld_safe[9255]: To do so, start the server, then issue the following commands:
Oct 29 08:21:11 ubuntu mysqld_safe[9255]: /usr/bin/mysqladmin -u root password 'new-password'
Oct 29 08:21:11 ubuntu mysqld_safe[9255]: /usr/bin/mysqladmin -u root -h ubuntu password 'new-password'
Oct 29 08:21:11 ubuntu mysqld_safe[9255]: See the manual for more instructions.
Oct 29 08:21:11 ubuntu mysqld_safe[9255]: Please report any problems with the /usr/bin/mysqlbug script!
Oct 29 08:21:11 ubuntu mysqld_safe[9255]: 
Oct 29 08:21:11 ubuntu mysqld_safe[9255]: The latest information about MySQL is available on the web at
Oct 29 08:21:11 ubuntu mysqld_safe[9255]: [http://www.mysql.com](http://www.mysql.com)
Oct 29 08:21:11 ubuntu mysqld_safe[9255]: Support MySQL by buying support/licenses at [http://shop.mysql.com](http://shop.mysql.com)
Oct 29 08:21:11 ubuntu mysqld_safe[9318]: ERROR: 1046  No database selected
Oct 29 08:21:11 ubuntu mysqld_safe[9318]: 081029  8:21:11 [ERROR] Aborting
Oct 29 08:21:11 ubuntu mysqld_safe[9318]: 
Oct 29 08:21:11 ubuntu mysqld_safe[9318]: 081029  8:21:11 [Note] /usr/sbin/mysqld: Shutdown complete
Oct 29 08:21:11 ubuntu mysqld_safe[9318]: 
Oct 29 08:21:11 ubuntu mysqld_safe[9410]: started
Oct 29 08:21:12 ubuntu mysqld[9413]: InnoDB: The first specified data file ./ibdata1 did not exist:
Oct 29 08:21:12 ubuntu mysqld[9413]: InnoDB: a new database to be created!
Oct 29 08:21:12 ubuntu mysqld[9413]: 081029  8:21:12  InnoDB: Setting file ./ibdata1 size to 10 MB
Oct 29 08:21:12 ubuntu mysqld[9413]: InnoDB: Database physically writes the file full: wait...
Oct 29 08:21:12 ubuntu mysqld[9413]: 081029  8:21:12  InnoDB: Log file ./ib_logfile0 did not exist: new to be created
Oct 29 08:21:12 ubuntu mysqld[9413]: InnoDB: Setting log file ./ib_logfile0 size to 5 MB
Oct 29 08:21:12 ubuntu mysqld[9413]: InnoDB: Database physically writes the file full: wait...
Oct 29 08:21:12 ubuntu mysqld[9413]: 081029  8:21:12  InnoDB: Log file ./ib_logfile1 did not exist: new to be created
Oct 29 08:21:12 ubuntu mysqld[9413]: InnoDB: Setting log file ./ib_logfile1 size to 5 MB
Oct 29 08:21:12 ubuntu mysqld[9413]: InnoDB: Database physically writes the file full: wait...
Oct 29 08:21:12 ubuntu mysqld[9413]: InnoDB: Doublewrite buffer not found: creating new
Oct 29 08:21:12 ubuntu mysqld[9413]: InnoDB: Doublewrite buffer created
Oct 29 08:21:12 ubuntu mysqld[9413]: InnoDB: Creating foreign key constraint system tables
Oct 29 08:21:12 ubuntu mysqld[9413]: InnoDB: Foreign key constraint system tables created
Oct 29 08:21:12 ubuntu mysqld[9413]: 081029  8:21:12  InnoDB: Started; log sequence number 0 0
Oct 29 08:21:12 ubuntu mysqld[9413]: 081029  8:21:12 [Note] /usr/sbin/mysqld: ready for connections.
Oct 29 08:21:12 ubuntu mysqld[9413]: Version: '5.0.45-Debian_1ubuntu3-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Debian etch distribution
Oct 29 08:21:12 ubuntu /etc/mysql/debian-start[9448]: Upgrading MySQL tables if necessary.
Oct 29 08:21:12 ubuntu /etc/mysql/debian-start[9453]: Looking for 'mysql' in: /cow/usr/bin/mysql
Oct 29 08:21:12 ubuntu /etc/mysql/debian-start[9453]: FATAL ERROR: Can't find '/cow/usr/bin/mysql'
Oct 29 08:21:12 ubuntu /etc/mysql/debian-start[9456]: Checking for insecure root accounts.
Oct 29 08:21:12 ubuntu /etc/mysql/debian-start[9462]: Checking for crashed MySQL tables.
Oct 29 08:21:34 ubuntu mysqld_safe[10166]: Number of processes running now: 1
Oct 29 08:21:34 ubuntu mysqld_safe[10174]: mysqld process hanging, pid 9412 - killed
Oct 29 08:21:34 ubuntu mysqld_safe[10177]: restarted
Oct 29 08:21:34 ubuntu mysqld[10180]: InnoDB: Unable to lock ./ibdata1, error: 11
Oct 29 08:21:34 ubuntu mysqld[10180]: InnoDB: Check that you do not already have another mysqld process
Oct 29 08:21:34 ubuntu mysqld[10180]: InnoDB: using the same InnoDB data or log files.
Oct 29 08:21:34 ubuntu mysqld[10180]: 081029  8:21:34  InnoDB: Retrying to lock the first data file
Oct 29 08:21:35 ubuntu mysqld[10180]: 081029  8:21:35  InnoDB: Database was not shut down normally!
Oct 29 08:21:35 ubuntu mysqld[10180]: InnoDB: Starting crash recovery.
Oct 29 08:21:35 ubuntu mysqld[10180]: InnoDB: Reading tablespace information from the .ibd files...
Oct 29 08:21:35 ubuntu mysqld[10180]: InnoDB: Restoring possible half-written data pages from the doublewrite
Oct 29 08:21:35 ubuntu mysqld[10180]: InnoDB: buffer...
Oct 29 08:21:35 ubuntu mysqld[10180]: 081029  8:21:35  InnoDB: Starting log scan based on checkpoint at
Oct 29 08:21:35 ubuntu mysqld[10180]: InnoDB: log sequence number 0 43655.
Oct 29 08:21:35 ubuntu mysqld[10180]: InnoDB: Doing recovery: scanned up to log sequence number 0 43655
Oct 29 08:21:35 ubuntu mysqld[10180]: 081029  8:21:35  InnoDB: Started; log sequence number 0 43655
Oct 29 08:21:35 ubuntu mysqld[10180]: 081029  8:21:35 [Note] Recovering after a crash using /var/log/mysql/mysql-bin
Oct 29 08:21:35 ubuntu mysqld[10180]: 081029  8:21:35 [Note] Starting crash recovery...
Oct 29 08:21:35 ubuntu mysqld[10180]: 081029  8:21:35 [Note] Crash recovery finished.
Oct 29 08:21:35 ubuntu mysqld[10180]: 081029  8:21:35 [Note] /usr/sbin/mysqld: ready for connections.
Oct 29 08:21:35 ubuntu mysqld[10180]: Version: '5.0.45-Debian_1ubuntu3-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Debian etch distribution

---

### Post by geirha on 2008-10-29
I don't have a good idea of what's going wrong here. Perhaps the lines are too long or something, though the dump is made with the same version of mysql, so one should expect it to be easily recovered. I'm out of ideas.

---

### Post by bronkeydain on 2008-10-29
Well you have given me loads of ideas already. I would have given up long ago.
Thank you for dedicating so much time trying to help a stranger!

I have signed up for a vTiger (it is a really good open source web based Customer Relation Management system) hosting account for like $130 for 2 years. It is not worth running your own server for these applications only. 

By the way I have asked my hosting company if they could upload my sqldump, but they require all the vTiger files from my server. No problem I thought.. I have a tar backup file... I mount my drive and start extracting the files from the tar file to another HD. Guess what... :lolflag: I get an error saying "attempt to access beyond end of device" lol here we go again.... I think I will just accept my data loss and get on with life... I'm gonna have a beer now.

---

