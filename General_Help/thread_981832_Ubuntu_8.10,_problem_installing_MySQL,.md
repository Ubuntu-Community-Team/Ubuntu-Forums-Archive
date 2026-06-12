---
title: "Ubuntu 8.10, problem installing MySQL,"
date: 2008-11-14
forum: General Help
---

### Post by bloup on 2008-11-14
Hi,

when I try to install MySQL in Ubuntu 8.10, I get the following message

```

bloup@zdkl:~$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mysql-server-5.0
Suggested packages:
  tinyca mailx
The following NEW packages will be installed:
  mysql-server mysql-server-5.0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 54.9kB/26.9MB of archives.
After this operation, 87.7MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://es.archive.ubuntu.com intrepid/main mysql-server 5.0.67-0ubuntu6 [54.9kB]
Fetched 54.9kB in 3s (17.0kB/s)
Preconfiguring packages ...
Selecting previously deselected package mysql-server-5.0.
(Reading database ... 106182 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.67-0ubuntu6_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.67-0ubuntu6_all.deb) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
Processing triggers for man-db ...
Setting up mysql-server-5.0 (5.0.67-0ubuntu6) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
Reloading AppArmor profiles : done.
 * Starting MySQL database server mysqld                                 [fail] 
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

If I try to run the mysqld, I get the following message:

```

bloup@zdkl:~$ sudo mysqld
081114 10:47:15  InnoDB: Started; log sequence number 0 43655
081114 10:47:15 [ERROR] Can't create IP socket: Permission denied
081114 10:47:15 [ERROR] Aborting

081114 10:47:15  InnoDB: Starting shutdown...
081114 10:47:16  InnoDB: Shutdown completed; log sequence number 0 43655
081114 10:47:16 [Note] mysqld: Shutdown complete

```

help would be appreciated!!

Thanks

---

### Post by Zhukov on 2008-11-14
Try this:

sudo apt-get -f install

sudo dpkg-reconfigure mysql-server-5.0

---

### Post by d-man97 on 2008-11-14
Zhukov has the right idea. It seems like you didn't go through the setup process where you set the MySQL root password, etc. Reconfiguring it will make you go through the simple GUI setup.

Additionally, there really is no reason to run MySQL with 'mysqld' from the command line. Edit /etc/mysql/my.cnf to make any changes to the server process. Then, run the mysql server like this:
```
$ sudo /etc/init.d/mysql start
```
'start' may also be replaced with 'stop' or 'restart', depending on what you want it to do. This is also done at boot time by the system, unless you disable it. After you have it installed OK, check out System > Administration > Services and you will see that 3 MySQL processes actually start with your system every time it boots.

Most server-type programs (daemons) are started like this.
Run the following to see which ones:
```
$ ls /etc/init.d/
```

Be careful though, restarting gdm, for example, will kick you out of your GUI session and send you back to the login screen (like Ctrl-Alt-Backspace). My rule: If I didn't install it, I won't stop/restart it.

---

### Post by bloup on 2008-11-14
Thank you for your replies.

well, i tried to call directly mysqld to see what was the error message that was preventing the installer to configure the package. The message from the installer is not really helping.

trying to reinstall the package with apt-get results in the same error. And since it is not configured, the /etc/init.d and dpkg-reconfigure scripts will not work.. :(

Thanks for your help.

---

### Post by Zhukov on 2008-11-16
Two things:

1 - Try removing and the install the package

2 - Download the package and force an install

---

### Post by wonkothesane on 2008-11-17
I had this problem, it actually appears to be a problem with apparmor blocking mysql's IP socket. I removed apparmor, and that solved the problem. There should be a better fix, though...

---

### Post by Zhukov on 2008-11-18
There are also some glitches with bind9. You have to check if the files are were they should be (and permissions).

---

