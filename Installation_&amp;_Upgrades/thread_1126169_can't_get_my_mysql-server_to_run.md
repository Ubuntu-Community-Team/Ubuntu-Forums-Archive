---
title: "can't get my mysql-server to run"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by gomenor on 2009-04-15
Hello!
I've a problem with getting my mysql-server to run. I think it has something to do with the "my.cnf" file and the "mysql(d).sock" file.
The lines in "my.cnf" assocciated with myqsl(d).sock are probably leading to the wrong destination. And the "mysql(d).sock file itself, is probably in the wrong directory to begin with.

I've looked at similar problems but not been able to find a solution. Reinstalling mysql-server doesn't work either:

```

jens@ubuntuserver:/$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  mysql-server-5.0
Suggested packages:
  tinyca mailx
The following NEW packages will be installed:
  mysql-server mysql-server-5.0
0 upgraded, 2 newly installed, 0 to remove and 190 not upgraded.
Need to get 0B/23.6MB of archives.
After this operation, 79.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 52525 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.75-0ubuntu10_i386.deb) ...
Aborting downgrade from (at least) 5.1 to 5.0.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.1.30really5.0.75-0ubuntu10_all.deb) ...
 * Stopping MySQL database server mysqld                                    [ OK ]
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

And when I try to run: ```
sudo mysql -u root -p

```

I get: ```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (2)
```

And this is how my "my.cnf" looks like. (The most important parts  anyways)

```

[client]
port            = 3306
socket          = /var/lib/mysql/mysql.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket          = /var/lib/mysql/mysql.sock
nice            = 0

[mysqld]
#
# * Basic Settings
#

#
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/lib/mysql/mysql.sock
port            = 3306
basedir         = /usr
datadir         = /media/data/mysql/mysql
tmpdir          = /tmp
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address            = 127.0.0.1

```

If someone could make any sence out of this, I would appritiate it :)

thank you guys

---

### Post by ahbart on 2009-04-15
I never had any problems with mysql server. If you install it from package manager it should run at startup. Make sure you remember the admin passsword. 
Right now you can try to remove mysql-server including configuration, by right clicking on the package in synaptic. And after a reboot (just to make sure) reinstall it via synaptic.
Oh and give mysql-admin a try. This is a very nice frontend.

---

### Post by guja on 2009-04-17
I have the same problem and I can't solve it no way. I try to delete, reinstall mysql-server, nothing helps.

Keep getting this:
```

Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

If anyone can help, I'd be very grateful!

---

### Post by corq on 2009-04-17
*bump* I'm having identical issue. Runs in safe mode, but won't accept connections. When I reinstall, I get what guja cites.

```
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by guja on 2009-04-18
Okay, I did dozens attempts to work something out, but nothing helped me.

I randomly typed this combination of commands and everything works for me now:
```

sudo apt-get autoremove
```

```
sudo apt-get --purge remove mysql-server

```
```
sudo apt-get update
```

```
sudo apt-get install mysql-server-5.1
```

After this, I have mysql server 5.1 which works fine, and apt isn't blocked anymore with that error report.

---

### Post by gomenor on 2009-04-21
```
 * Starting MySQL database server mysqld                                 [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up postfix (2.5.5-1.1) ...

Postfix was not set up.  Start with
  cp /usr/share/postfix/main.cf.debian /etc/postfix/main.cf
.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.


Setting up bsd-mailx (8.1.2-0.20081101cvs-2ubuntu1) ...

Setting up mailx (1:20081101-2ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 mysql-server-5.1
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Getting this error message when I tried your tip "Guja". I think it's because some files isn't included when I try to do the "remove" command. For example, the cnf and .sock files. Can those files somehow be restored, so I can get a COMPLETLY fresh mysql-server installation.

---

### Post by Senior_X on 2009-05-06
to gomenor and corq
I have had heaps of trouble with deinstalling and trying to reinstall mysql server on Ubuntu 8.10, by means of the  synaptic packet manager. It just can't be done, I have searched every forum on this planet. 

Then I did the following: removed everything named "mysql" and the like, and installed the community server (the tar.gz file), and unpacked it. Now I  can start the server manually by typing ./mysql.server start, BUT ONLY AS THE MYSQL USER, not as root/administrator. I have created links to the init.d script in rc0.d and rc2.d (rc2.d is the Ubuntu default run level), but the script never gets executed, because it is not run as mysql user.
Now here is what I found out, hopefully it might give you some clues, too:
the mysql.sock file, which is causing a lot of error messages all over the world, is a file which is created when the server is successfully started. No wonder many people get this message, and nobody cares to give them the reason why. Another point: there are also a great number of error messages concerning a "failed subscript". I get these messages when I try to execute as "the wrong user". For me it is really a great great pain in a certain part of my body, constantly being forced to deal with these inferior user problems- I am the only person using my home-network, what do I care about root and non-roots? Another mystery is the default shell for the mysql-user, if you install using synaptic, It is /bin/false, and if I now  use this as the default shell for the mysql user, I get a "failed subscript" error message, when I try to start the server maually. But if I change this shell to /bin/bash, I can run the mysql server. I  AM JUST UNABLE TO COMPREHEND, I AM TOTALLY & COMPLETELY UNABLE TO COMPREHEND.
 Now can anyone please tell me: 
HOW CAN I  EXECUTE THE START-UP SCRIPT WHEN THE COMPUTER IS BOOTING (having mysql start automatically)?. I have got a working script, but it only works when I am "su'ing" to the mysql user, which owns the data subdirectory of mysql, and then execute the script. Then links in /etc/rc... do not work.
by the way: apparmour might be a cause of complication, too. I wish it could be thrown out.
bye
Senior_X

---

### Post by josealfredo1515 on 2011-05-16
I commented "skip-bdb" in my.cnf and it worked!

---

