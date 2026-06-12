---
title: "Need help setting up Bacula"
date: 2008-08-19
forum: General Help
---

### Post by voodoobettie on 2008-08-19
Hi everyone, 

(Apologies mods if this is in the wrong forum, the server platform forum would not load)

Please excuse my newbiness, but I'm desperately trying to get bacula working so that I can back up some windows shares. We recently had a power failure and had 3 of our 5 servers fail (including the backup server) so I'm desperately trying to get this running before anything else breaks. :KS

I am running Hardy Heron (2.6.24-19-server) & I need to back up an Exchange mail server and mailboxes, Windows shares and a MS SQL 2000 database. I have an HP Ultrium DLT drive. I tried following the bacula.org docs but it seems that Ubuntu is missing some of the config files. I used synaptic to install bacula and the bacula-dir.conf was missing so I created it from scratch based the doc at [https://help.ubuntu.com/8.04/serverguide/C/bacula.html](https://help.ubuntu.com/8.04/serverguide/C/bacula.html) - however, when I try to start bacula-dir I get the error message below and I can't figure out where I went wrong:  

* Stopping Bacula Director:                                             [ OK ]
 * Starting Bacula Director:                                                    19-Aug 12:31 bacula-dir: ERROR TERMINATION at parse_conf.c:483
Config error: Could not find config Resource DefaultJob referenced on line 7 :  JobDefs = "DefaultJob"


            : line 7, col 24 of file /etc/bacula/bacula-dir.conf
        JobDefs = "DefaultJob"


My bacula-dir.conf looks like this:

#
# Define the nightly save backup job
# By default this job will back up to disk

 Job {
        Name = "LocalhostBackup-test"
        JobDefs = "DefaultJob"
        Write Bootstrap = "/var/lib/bacula/Client1.bsr"
 }

#
# Definition of "Tape Drive" storage device

Storage {

  Name = TapeDrive

  # Do not use localhost here, use FQDN

  Address = velouria

  SDPort = 9103

  Password = "Cv70F6pf1t6pBopT4vQOnigDrR0v3LT3Cgkiyj"

  Device = "Tape Drive"

  Media Type = tape
}

#
# LocalhostBackup FileSet

FileSet {

  Name = "LocalhostFiles"
  Include {
        Options {
        signature = MD5
        compression = GZIP
        }
        File = /etc
        File = /home
        }
  }

#
# LocalhostBackup Schedule -- Daily

Schedule {
        Name = "LocalhostDaily"
        Run = Full daily at 00:01
}


#
# Create job for Localhost backup

Job {
        Name = "LocalhostBackup"
        JobDefs = "DefaultJob"
        Enabled = yes
        Level = Full
        FileSet = "LocalhostFiles"
        Schedule = "LocalhostDaily"
        Storage = "TapeDrive"
        Write Bootstrap = "/var/lib/bacula/LocalhostBackup.bsr"
}


And my bacula-sd.conf device config looks like this:

Device {
  Name = "Tape Drive"
  Device Type = tape
  Media Type = DLT
  Archive Device = /dev/st0
  Hardware end of medium = No;
  LabelMedia = yes;                   # lets Bacula label unlabeled media
  RandomAccess = no;
  AutomaticMount = yes;               # when device opened, read it
  RemovableMedia = yes;
  AlwaysOpen = Yes;
  Alert Command = "sh -c 'tapeinfo -f %c | grep TapeAlert'"
}


These are the packages I have installed.

bettie@velouria:~$ bettie@velouria:~$ dpkg -l | grep bacula
ii  bacula                                2.2.8-5ubuntu7                           Network backup, recovery and verification (M
ii  bacula-client                         2.2.8-5ubuntu7                           Network backup, recovery and verification (C
ii  bacula-common                         2.2.8-5ubuntu7                           Network backup, recovery and verification (C
ii  bacula-console                        2.2.8-5ubuntu7                           Network backup, recovery and verification (M
ii  bacula-console-qt                     2.2.8-5ubuntu7                           network backup, recovery and verification -
ii  bacula-director-common                2.2.8-5ubuntu7                           Network backup, recovery and verification (D
ii  bacula-director-mysql                 2.2.8-5ubuntu7                           Network backup, recovery and verification (D
ii  bacula-doc                            2.2.5-1                                  Documentation for Bacula
ii  bacula-fd                             2.2.8-5ubuntu7                           Network backup, recovery and verification (F
ii  bacula-sd                             2.2.8-5ubuntu7                           Network backup, recovery and verification (S
ii  bacula-sd-mysql                       2.2.8-5ubuntu7                           Network backup, recovery and verification (S
ii  bacula-server                         2.2.8-5ubuntu7                           Network backup, recovery and verification (S
ii  bacula-traymonitor                    2.2.8-5ubuntu7                           Network backup, recovery and verification (T


Ideally I'd like to use the gnome console and system tray monitor but at this point I'll pretty much take anything. Thanks all for helping a sad sysadmin gal out.

~ Bettie

---

### Post by voodoobettie on 2008-08-20
Okay I have made some progress since yesterday. I found another thread that suggested that installing mySQL first was the way to go so I've done a full reinstall and I installed the bacula packages with apt instead of synaptic this time. I built a very basic bacula config and I was able to start the bacula daemons and now I'm trying to get the monitor (bacula-tray-monitor) to work and when I try to start it (using sudo) I get an error that says: 

20-Aug 15:41 tray-monitor: ERROR TERMINATION at parse_conf.c:829
Config error: Cannot open config file "./tray-monitor.conf": No such file or directory

I have a tray-monitor.conf and a bat.conf file (below) so I can't figure out what it wants. Any help would be greatly appreciated! :)

#
# Bacula Tray Monitor Configuration File
#

Monitor {
  Name = localhost-mon
  Password = "xyz"         # password for the Directors   
  RefreshInterval = 5 seconds
}
   
Client {
  Name = localhost-fd
  Address = localhost
  FDPort = 9102
  Password = "xyz"          # password for FileDaemon
}

Storage {
  Name = localhost-sd
  Address = localhost
  SDPort = 9103
  Password = "xyz"          # password for StorageDaemon
}

Director {
  Name = localhost-dir
  DIRport = 9101
  address = localhost
}



#
# Bacula Administration Tool (bat) configuration file
#

Director {
  Name = localhost-dir
  DIRport = 9101
  address = localhost
  Password = "xyz"
}

---

### Post by fredfox on 2008-08-22
If you are running the command:

> sudo bacula-tray-monitor

it is looking in your present working directory to find the configuration file, so that command will only work if you run it from /etc/bacula. Try the following

>  sudo bacula-tray-monitor -f /etc/bacula/tray-monitor.conf

---

### Post by manthony121 on 2008-08-24
I am also trying to get bacula running.  The default config files, including bacula-dir.conf, are in the "usr/share/bacula-common/defconfig".  I copied them to the "/etc/bacula" directory, then edited them by hand to set the correct Name, Address directives.  However, I still don't have my setup working, so I make no claims to know what I'm doing!

---

### Post by manthony121 on 2008-08-24
SUCCESS!!!

I just finished getting bacula running on my Ubuntu 8.04 system, and did a successful backup/restore cycle.  Here's what it took:

I installed using Synaptic: bacula, bacula-client, bacula-common, bacula-console, bacula-director-common, bacula-director-mysql, bacula-doc, bacula-fd, bacula-sd, bacula-sd-mysql, bacula-server, bacula-traymonitor.  I am using mySQL for the database, and have these packages also installed: mysql-admin, mysql-client, mysql-client-5.0, mysql-common, mysql-doc-5.0, mysql-gui-tools-common, mysql-server, and mysql-server-5.0.

Before you worry about bacula, you have to make sure that you have mysql set up correctly.  The bacula source tree includes several scripts that make this automatic, but they don't come with the Synaptic packages.  So, get the bacula source (bacula-2.4.2.tar.gz), put it somewhere out of the way (I have a directory, /opt, for such things), unpack it (tar xzvf bacula-2.4.2.tar.gz), then cd to the bacula-2.4.2/src/cats, and copy the following scripts to your /etc/bacula/scripts directory:  create_mysql_database.in, drop_mysql_tables.in, grant_mysql_privileges.in, and make_mysql_tables.in.  You also have to perform "chmod +x *.in" if they are not already flagged as executables.

These scripts have some variables that you will need to set by hand, since we are not running the Makefile that would do it for you.  Each script has, near the top, lines such as:

USER=@db_user@
bindir=@SQL_BINDIR@
db_name=@db_name@

Change these to:

USER=bacula
bindir=/usr/bin
db_name=bacula

I did some work on mySQL by hand, but these scripts should do the trick.  Run them in this sequence:

grant_mysql_privileges.in
create_mysql_database.in
make_mysql_tables.in

BTW, I do NOT have passwords set on any of the mySQL accounts.  I will have to fix that later, and hope that it isn't too hard to fix whatever breaks.

Hopefully, at this point, mySQL is set up and waiting for some data to eat.  It's time to start working on bacula itself.

The default config files for bacula are in the directory, "/usr/share/bacula-common/defconfig".  Copy them to /etc/bacula, then edit them.

Each config file has tags, such as "Name = @hostname@-dir", that all have to agree with each other.  Change each instance of "@hostname@" to the real hostname as follows:

sed 's/@hostname@/acer/' bacula-dir.conf > bacula-dir.x
mv bacula-dir.x bacula-dir.conf

Do that for each of the config files, using whatever name you like in place of 'acer' (I'm doing this on an Acer laptop, in case you were wondering).  In 'bacula-dir.conf' there is also a line under "Catalog {":
dbname = bacula; user = @db_user@; password = "@db_pswd@"

Change it to:

dbname = bacula; user = bacula; password = ""

Another edit to be made is to define what files you want to backup:

(In bacula-dir.conf):
...
FileSet {
  Name = "Full Set"
  Include {
    Options {
      signature = MD5
    }
    File = /opt
  }
  Exclude {
    File = /proc
    File = /tmp
    File = /.journal
    File = /.fsck
  }
}
...

Here, I am just backing up my "/opt" directory as a test.

(In the actual conf file, these lines are nicely indented, but the indentations are lost when posting this message)

Another issue with the config files is the specification of Addresses, as in the section:
Storage {
  Name = File
  Address = acer
  ...

According to someone on a different thread (assuming that all the parts of bacula are going to be running on the same machine), set all the Address specifications in each of the config files to "127.0.0.1"

The final "gotcha" is a port conflict with some HP printer software.  It just so happens that I use HP printers on my home network, and couldn't get bacula to work without changing default ports.  HP uses port 9102, so bacula-fd can't.  In bacula-dir.conf, do this:

Client {
  ...
  FDPort = 9104
  ...

You will also have to change the port number in the other config files:

bacula-fd.conf:
...
FileDaemon {
  ...
  FDport = 9104
  ...
}

tray-monitor.conf:
...
Client {
  ...
  FDPort = 9104
  ...
}


FINALLY....(re)start all the daemons in /etc/init.d/:
/etc/init.d/bacula-director restart
/etc/init.d/bacula-fd restart
/etc/init.d/bacula-sd restart

Fire up 'bconsole', and start the testing, as described in Chapter 9 (A Brief Tutorial) of the User Manual.  Hopefully, you'll be able to do a backup and restore as the chapter describes.

That's as far as I have gotten.  My next goal is to get it working over a network, backing up different clients with different OSes.  Stay tuned, and...Good luck!

---

### Post by voodoobettie on 2008-08-25
Thanks so much for the replies, hopefully this will alleviate my frustration. I'm going to do as you suggested and I'll let you know how it goes. :)

Wish me luck!

---

### Post by iskatyel on 2008-10-07
Has anyone logged a bug for this?  The /etc/bacula/bacula-dir.conf is apparently expected from the documentation [https://help.ubuntu.com/community/Bacula](https://help.ubuntu.com/community/Bacula) and [https://help.ubuntu.com/8.04/serverguide/C/bacula.html](https://help.ubuntu.com/8.04/serverguide/C/bacula.html) with no explanation of where to find it for new users.  This file should be present.  
Thanks for the success story!

---

### Post by iskatyel on 2008-10-09
I think the HP port issue is restricted to print servers that have multiple ports.  The normal HP raw network printer port is 9100.  I had to make a couple of slight modifications to the instructions above and I did the mysql stuff with passwords on a fresh install of Ubuntu 8.04.1 Server AMD64 and this is what I had to do:

Install the package and download the source:
```
apt-get install bacula-server bacula-console bacula-director-mysql
wget -c [http://downloads.sourceforge.net/bacula/bacula-2.4.2.tar.gz?modtime=1217191248&big_mirror=1](http://downloads.sourceforge.net/bacula/bacula-2.4.2.tar.gz?modtime=1217191248&big_mirror=1)
```

Copy the db creation scripts over from the source package and replace the generic bits.
```
sed 's/@db_user@/bacula/;s/@SQL_BINDIR@/\/usr\/bin/;s/@db_name@/bacula/;s/ -f </ -f -p </' /usr/src/bacula-2.4.2/src/cats/grant_mysql_privileges.in > /etc/bacula/scripts/grant_mysql_privileges.in
sed 's/@db_user@/bacula/;s/@SQL_BINDIR@/\/usr\/bin/;s/@db_name@/bacula/;s/ -f </ -f -p </' /usr/src/bacula-2.4.2/src/cats/create_mysql_database.in > /etc/bacula/scripts/create_mysql_database.in
sed 's/@db_user@/bacula/;s/@SQL_BINDIR@/\/usr\/bin/;s/@db_name@/bacula/;s/ -f </ -f -p </' /usr/src/bacula-2.4.2/src/cats/make_mysql_tables.in > /etc/bacula/scripts/make_mysql_tables.in
chmod +x /etc/bacula/scripts/create_mysql_database.in  /etc/bacula/scripts/grant_mysql_privileges.in /etc/bacula/scripts/make_mysql_tables.in
```

Run the scripts:
```
./grant_mysql_privileges.in
./create_mysql_database.in
./make_mysql_tables.in 
```

Modify and copy over missing bacula-dir.conf
```
sed 's/@db_user@/bacula/;s/@db_name@/bacula/;s/@hostname@/example/' /usr/share/bacula-common/defconfig/bacula-dir.conf > /etc/bacula/bacula-dir.conf
chmod 640 /etc/bacula/bacula-dir.conf
chown bacula.bacula /etc/bacula/bacula-*
```

Set bacula user's password (replace @db_pswd@):
```
mysql -u root -p bacula
set password for 'bacula'@'localhost' = password('@db_pswd@');
quit
```

Edit the .conf files to start system:
```
nano /etc/bacula/bacula-dir.conf 
# out DirAddress
on line 236: enter the password:
dbname = bacula; user = bacula; password = "@db_pswd@ " and enter the password
update BackupCatalog job with actual catalog name MyCatalog on line 69
change backup files to something with content for testing on line 114
provide FQDN for address on line 189

nano /etc/bacula/bacula-sd.conf
# out sdAddress
set archive device under filesystem storage:
archive device = /var/lib/bacula/bckp
chown bacula.bacula /var/lib/bacula/bckp
then mkdir /var/lib/bacula/bckp

nano /etc/bacula/bacula-fd.conf 
# out fdAddress
/etc/init.d/bacula-director restart
/etc/init.d/bacula-fd restart
/etc/init.d/bacula-sd restart
```

Start bconsole and test the setup:
```
bconsole
label
run
```

---

### Post by linuxcorp on 2009-01-28
Hi There

I have been reading the posts about setting up bacula and so far its been going ok, but...... the mysql part is where i'm stuck at.

I copied the scripts create_mysql_database.in, drop_mysql_tables.in, grant_mysql_privileges.in and make_mysql_tables.in. 

I then edited grant_mysql_privileges.in like this:

#!/bin/sh
#
# shell script to grant privileges to the bacula database
#
db_user=${bacula}
bindir=/usr/bin
db_name=${bacula}

if $bindir/mysql $* -u root -f -p <<END-OF-DATA
use mysql
grant all privileges on ${db_name}.* to ${db_user}@localhost;
grant all privileges on ${db_name}.* to ${db_user}@"%";
select * from user;
flush privileges;
END-OF-DATA
then
   echo "Privileges for ${db_user} granted on ${db_name}."
   exit 0
else
   echo "Error creating privileges."
   exit 1
fi

Saved it and ran it and it gave me :

root@ubuntu:/etc/bacula/scripts# ./grant_mysql_privileges.in
Enter password:

I put the password in and :


ERROR 1064 (42000) at line 2: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '* to @localhost' at line 1
ERROR 1064 (42000) at line 3: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '* to @"%"' at line 1
Host    User    Password        Select_priv     Insert_priv     Update_priv     Delete_priv     Create_priv     Drop_priv       Reload_priv     Shutdown_privProcess_priv    File_priv       Grant_priv      References_priv Index_priv      Alter_priv      Show_db_priv    Super_priv      Create_tmp_table_priv   Lock_tables_priv     Execute_priv    Repl_slave_priv Repl_client_priv        Create_view_priv        Show_view_priv  Create_routine_priv     Alter_routine_priv  Create_user_priv ssl_type        ssl_cipher      x509_issuer     x509_subject    max_questions   max_updates     max_connections max_user_connections
localhost       root    *745474B48363C1C70F08D740912F0C8309223CB1       Y       Y       Y       Y       Y       Y       Y       Y       Y       Y       Y   YY       Y       Y       Y       Y       Y       Y       Y       Y       Y       Y       Y       Y       Y                                       0       0   00
ubuntu  root    *745474B48363C1C70F08D740912F0C8309223CB1       Y       Y       Y       Y       Y       Y       Y       Y       Y       Y       Y       Y   YY       Y       Y       Y       Y       Y       Y       Y       Y       Y       Y       Y       Y                                       0       0       0   0
127.0.0.1       root    *745474B48363C1C70F08D740912F0C8309223CB1       Y       Y       Y       Y       Y       Y       Y       Y       Y       Y       Y   YY       Y       Y       Y       Y       Y       Y       Y       Y       Y       Y       Y       Y       Y                                       0       0   00
localhost                       N       N       N       N       N       N       N       N       N       N       N       N       N       N       N       N   NN       N       N       N       N       N       N       N       N                                       0       0       0       0
ubuntu                  N       N       N       N       N       N       N       N       N       N       N       N       N       N       N       N       N   NN       N       N       N       N       N       N       N                                       0       0       0       0
localhost       debian-sys-maint        *6C549AD0545BD1D577AC1CE19B547072E58DC6DA       Y       Y       Y       Y       Y       Y       Y       Y       Y   YY       Y       Y       Y       Y       Y       Y       Y       Y       Y       Y       N       N       N       N       N                                   00       0       0
Privileges for  granted on .
root@ubuntu:/etc/bacula/scripts#

It says it granted the privileges but there are errors ?.

Then i edited the create_mysql_database.in like this:  

#!/bin/sh
#
# shell script to create Bacula database(s)
#

bindir=/usr/bin/
db_name=bacula

if $bindir/mysql $* -u root -f -p <<END-OF-DATA
CREATE DATABASE ${bacula};
END-OF-DATA
then
   echo "Creation of ${db_name} database succeeded."
else
   echo "Creation of ${db_name} database failed."
fi
exit 0

Saved it and ran it and it gave me : 

root@ubuntu:/etc/bacula/scripts# ./create_mysql_database.in
Enter password:

ok so i put the root password in and :

ERROR 1064 (42000) at line 1: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 1
Creation of bacula database succeeded.

I said it created the database but what is the error for ?.


Then i edited the make_mysql_tables.in like this:

#!/bin/sh
#
# shell script to create Bacula MySQL tables
#
bindir=/usr/bin
db_name=${bacula}

if $bindir/mysql $* -u root -f -p <<END-OF-DATA
USE ${db_name};

Saved it and ran it and it gave me this :

root@ubuntu:/etc/bacula/scripts# ./make_mysql_tables.in
Enter password:

ok so i put the root password in and :

Creation of Bacula MySQL tables succeeded.
root@ubuntu:/etc/bacula/scripts#

Ok so now i run the following command :

root@ubuntu:/etc/bacula/scripts# mysql -u root -p bacula
Enter password:

I put in the password and i get :

Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 23
Server version: 5.0.51a-3ubuntu5.4 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>

At the mysql prompt i put in :

mysql> set password for 'bacula'@'localhost' = password('my-password');

and i get the following message : 

ERROR 1133 (42000): Can't find any matching row in the user table

Confused.........

Status command gives me :

mysql> status
--------------
mysql  Ver 14.12 Distrib 5.0.51a, for debian-linux-gnu (i486) using readline 5.2

Connection id:          23
Current database:       bacula
Current user:           root@localhost
SSL:                    Not in use
Current pager:          stdout
Using outfile:          ''
Using delimiter:        ;
Server version:         5.0.51a-3ubuntu5.4 (Ubuntu)
Protocol version:       10
Connection:             Localhost via UNIX socket
Server characterset:    latin1
Db     characterset:    latin1
Client characterset:    latin1
Conn.  characterset:    latin1
UNIX socket:            /var/run/mysqld/mysqld.sock
Uptime:                 1 hour 32 min 20 sec

Threads: 1  Questions: 173  Slow queries: 0  Opens: 57  Flush tables: 1  Open tables: 27  Queries per second avg: 0.031
--------------

mysql>

I exit the shell and try to login with the user bacula :

root@ubuntu:/etc/bacula/scripts# mysql -u bacula -p
Enter password:
ERROR 1045 (28000): Access denied for user 'bacula'@'localhost' (using password: YES)
root@ubuntu:/etc/bacula/scripts#

But no luck

So i tried this command :

root@ubuntu:/etc/bacula/scripts# mysql -u bacula -p bacula
Enter password:
ERROR 1045 (28000): Access denied for user 'bacula'@'localhost' (using password: YES)
root@ubuntu:/etc/bacula/scripts#

Same problem...

Please can some one help me.

---

