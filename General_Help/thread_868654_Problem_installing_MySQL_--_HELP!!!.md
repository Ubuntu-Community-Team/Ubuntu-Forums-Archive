---
title: "Problem installing MySQL -- HELP!!!"
date: 2008-07-24
forum: General Help
---

### Post by mb_webguy on 2008-07-24
I recently fubar'ed Gnome (or possibly X) and decided to do a clean install of Ubuntu 8.04 to fix that as well as some lingering configuration problems I've had since upgrading from Gutsy.  I have a good partitioning setup, so it was fairly painless for the most part.

However, I've run into a snag installing MySQL.  The first time I tried installing it, everything seemed to go fine until I tried to log in using MySQL Administrator, which gave me the error:

```
Could not connect to host 'localhost'.
MySQL Error Nr. 2002
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

Running "sudo find / -name "mysqld.sock"" in the terminal gives no results -- the file doesn't exist.  So I figured something must have gone wrong with the installation.  So I type "sudo apt-get autoremove --purge mysql-server mysql-server-5.0" to get rid of the previous installation, and then "sudo apt-get install mysql-server" to reinstall.  That gives me the following output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl mysql-client-5.0 mysql-server-5.0
Suggested packages:
  dbishell libcompress-zlib-perl mysql-doc-5.0 tinyca
Recommended packages:
  libhtml-template-perl mailx
The following NEW packages will be installed:
  libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl mysql-client-5.0 mysql-server mysql-server-5.0
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/36.3MB of archives.
After this operation, 107MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package libnet-daemon-perl.
(Reading database ... 134066 files and directories currently installed.)
Unpacking libnet-daemon-perl (from .../libnet-daemon-perl_0.38-1.1_all.deb) ...
Selecting previously deselected package libplrpc-perl.
Unpacking libplrpc-perl (from .../libplrpc-perl_0.2017-1.1_all.deb) ...
Selecting previously deselected package libdbi-perl.
Unpacking libdbi-perl (from .../libdbi-perl_1.601-1_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.005-1_i386.deb) ...
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.51a-3ubuntu5.1_i386.deb) ...
Selecting previously deselected package mysql-server-5.0.
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.51a-3ubuntu5.1_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.51a-3ubuntu5.1_all.deb) ...
Setting up libnet-daemon-perl (0.38-1.1) ...
Setting up libplrpc-perl (0.2017-1.1) ...
Setting up libdbi-perl (1.601-1) ...
Setting up libdbd-mysql-perl (4.005-1) ...
Setting up mysql-client-5.0 (5.0.51a-3ubuntu5.1) ...
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                                                                                   [ OK ] 
080724  2:46:52 [Warning] Can't create test file /usr/share/mysql/the-tardis.lower-test
080724  2:46:52 [Warning] Can't create test file /usr/share/mysql/the-tardis.lower-test
ERROR: 1146  Table 'mysql.user' doesn't exist
080724  2:46:52 [ERROR] Aborting

080724  2:46:52 [Note] /usr/sbin/mysqld: Shutdown complete

Reloading AppArmor profiles : done.
 * Starting MySQL database server mysqld                                                                                                   [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So I purge mysql-server and mysql-server-5.0 again, and this time try "sudo apt-get install mysql-server-5.0", thinking that since the metapackage is having a dependency problem I just cut out the middleman.  This gives me the following output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl mysql-client-5.0
Suggested packages:
  dbishell libcompress-zlib-perl mysql-doc-5.0 tinyca
Recommended packages:
  libhtml-template-perl mailx
The following NEW packages will be installed:
  libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl mysql-client-5.0 mysql-server-5.0
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/36.2MB of archives.
After this operation, 107MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package libnet-daemon-perl.
(Reading database ... 134066 files and directories currently installed.)
Unpacking libnet-daemon-perl (from .../libnet-daemon-perl_0.38-1.1_all.deb) ...
Selecting previously deselected package libplrpc-perl.
Unpacking libplrpc-perl (from .../libplrpc-perl_0.2017-1.1_all.deb) ...
Selecting previously deselected package libdbi-perl.
Unpacking libdbi-perl (from .../libdbi-perl_1.601-1_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.005-1_i386.deb) ...
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.51a-3ubuntu5.1_i386.deb) ...
Selecting previously deselected package mysql-server-5.0.
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.51a-3ubuntu5.1_i386.deb) ...
Setting up libnet-daemon-perl (0.38-1.1) ...
Setting up libplrpc-perl (0.2017-1.1) ...
Setting up libdbi-perl (1.601-1) ...
Setting up libdbd-mysql-perl (4.005-1) ...
Setting up mysql-client-5.0 (5.0.51a-3ubuntu5.1) ...
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                                                                                   [ OK ] 
080724  2:50:59 [Warning] Can't create test file /usr/share/mysql/the-tardis.lower-test
080724  2:50:59 [Warning] Can't create test file /usr/share/mysql/the-tardis.lower-test
ERROR: 1146  Table 'mysql.user' doesn't exist
080724  2:50:59 [ERROR] Aborting

080724  2:50:59 [Note] /usr/sbin/mysqld: Shutdown complete

Reloading AppArmor profiles : done.
 * Starting MySQL database server mysqld                                                                                                   [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

*Sigh*  There's *still* no mysqld.sock file, and I still get the same error when I try to connect to MySQL.  I've tried creating a mysqld.sock file in the appropriate directory (using "touch"), but it didn't seem to have any effect.  I *really* need to get MySQL up and running again.  Help me please!

---

### Post by justleen on 2008-07-24
try a "dpkp -- reconfigure mysql-server-5.0"

after that, do a manual "/etc/init.d/mysqld restart". see if it starts without errors.

---

### Post by danwood76 on 2008-07-24
The .sock file should be cre4ated when the mysqld starts, so as justleen said reconfiguring it might help.

I would stop the mysqld and start it from the terminal without daemonising it looking for errors as this will point to what is wrong.
There may also be hints in the mysql logs.

---

### Post by mb_webguy on 2008-07-24
"sudo dpkg --configure mysql-server-5.0" gives me:

```
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                                               [ OK ] 
080724  5:43:04 [Warning] Can't create test file /usr/share/mysql/the-tardis.lower-test
080724  5:43:04 [Warning] Can't create test file /usr/share/mysql/the-tardis.lower-test
ERROR: 1146  Table 'mysql.user' doesn't exist
080724  5:43:04 [ERROR] Aborting

080724  5:43:04 [Note] /usr/sbin/mysqld: Shutdown complete

Reloading AppArmor profiles : done.
 * Starting MySQL database server mysqld                                                               [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0

```

"sudo mysqld" gives me:

```
080724  5:49:12 [Warning] Can't create test file /usr/share/mysql/the-tardis.lower-test
080724  5:49:12 [Warning] Can't create test file /usr/share/mysql/the-tardis.lower-test
080724  5:49:12  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'create'.
InnoDB: Cannot continue operation.

```

However, I've checked the /usr/share/mysql directory.  It's owned by the mysql user, with 755 permissions.  MySQL shouldn't have any problem creating a file in that folder.  Since it doesn't seem like MySQL isn't really starting (even though the service will start), I still don't have a mysqld.sock file, nor any log files.

---

### Post by danwood76 on 2008-07-24
> **mb_webguy said:**
>  * Starting MySQL database server mysqld                                                               [fail]

That indicates mysql isnt starting properly due to the errors above.

Remove mysql using the 'complete removal' option in synaptic and make sure the mysql dirs are deleted.

Then reinstall it, btw this will delete any databases you have so make sure you back them up first,

---

### Post by mb_webguy on 2008-07-24
Ok, I finally got MySQL to start -- by doing *another* clean install of the OS.  I don't know what was wrong, but some permissions must have gotten fubar'ed during the earlier install.

However, I still have a bit of a problem.  I previously had my MySQL datadir located on an NTFS partition shared between Windows and Ubuntu.  Since NTFS doesn't handle Unix-type permissions, the whole thing is currently mounted as uid=1000 (my username), gid=1001 (a newly created user group), and umask=000 (giving universal read/write/execute permissions, which is terrible security and hopefully temporary if I can get this frakking MySQL to work).

Despite this, if I reassign the MySQL datadir to point to the directory on the NTFS partition (which I had previously been using with no problem before I stupidly decided to do the clean install), MySQL won't start, giving the errors:

```
080724 18:30:45 [Warning] Can't create test file /media/Data/Big/db/the-tardis.lower-test
080724 18:30:45 [Warning] Can't create test file /media/Data/Big/db/the-tardis.lower-test
080724 18:30:45  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.

```

/media/Data/Big is the NTFS partition, and db is the intended datadir.  As I said, the entire partition has permissions of 777, so there really shouldn't be any problems with "access rights".  Also, that I'm trying to put the datadir on an NTFS partition shouldn't matter, since I did it before.  For the time being, I can deal with not being able to access MySQL from Windows, but I'll eventually need to do so.  

I suppose I could write a script or two that copies the database files from the Ubuntu datadir to the Windows datadir on shutdown, and from the Windows datadir to the Ubuntu datadir on startup, but that's a really suboptimal solution, especially since I had this working before...

---

### Post by killman.lt on 2008-11-06
Stepped onto the same problem again. But some research (a.k.a. Google) pointed in the right direction.

I was getting errors like this in my syslog:
```
Nov  6 12:13:02 FrontIT-Marijus mysqld_safe[6327]: started
Nov  6 12:13:02 FrontIT-Marijus kernel: [  188.051513] __ratelimit: 3 callbacks suppressed
Nov  6 12:13:02 FrontIT-Marijus kernel: [  188.051522] type=1503 audit(1225966382.852:20): operation="inode_create" requested_mask="a::" denied_mask="a::" fsuid=0 name="/media/Data/MySQL/Datafiles/FrontIT-Marijus.lower-test" pid=6329 profile="/usr/sbin/mysqld"
Nov  6 12:13:02 FrontIT-Marijus mysqld[6331]: 081106 12:13:02 [Warning] Can't create test file /media/Data/MySQL/Datafiles/FrontIT-Marijus.lower-test
Nov  6 12:13:02 FrontIT-Marijus kernel: [  188.057466] type=1503 audit(1225966382.860:21): operation="inode_create" requested_mask="a::" denied_mask="a::" fsuid=0 name="/media/Data/MySQL/Datafiles/FrontIT-Marijus.lower-test" pid=6329 profile="/usr/sbin/mysqld"
Nov  6 12:13:02 FrontIT-Marijus mysqld[6331]: 081106 12:13:02 [Warning] Can't create test file /media/Data/MySQL/Datafiles/FrontIT-Marijus.lower-test
Nov  6 12:13:02 FrontIT-Marijus kernel: [  188.084875] type=1503 audit(1225966382.888:22): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=112 name="/media/Data/MySQL/Datafiles/ibdata1" pid=6329 profile="/usr/sbin/mysqld"
Nov  6 12:13:02 FrontIT-Marijus mysqld[6331]: 081106 12:13:02  InnoDB: Operating system error number 13 in a file operation.
Nov  6 12:13:02 FrontIT-Marijus mysqld[6331]: InnoDB: The error means mysqld does not have the access rights to
Nov  6 12:13:02 FrontIT-Marijus mysqld[6331]: InnoDB: the directory.
Nov  6 12:13:02 FrontIT-Marijus mysqld[6331]: InnoDB: File name ./ibdata1
Nov  6 12:13:02 FrontIT-Marijus mysqld[6331]: InnoDB: File operation call: 'open'.
Nov  6 12:13:02 FrontIT-Marijus mysqld[6331]: InnoDB: Cannot continue operation.
Nov  6 12:13:02 FrontIT-Marijus mysqld_safe[6337]: ended
Nov  6 12:13:17 FrontIT-Marijus /etc/init.d/mysql[6490]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Nov  6 12:13:17 FrontIT-Marijus /etc/init.d/mysql[6490]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Nov  6 12:13:17 FrontIT-Marijus /etc/init.d/mysql[6490]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Nov  6 12:13:17 FrontIT-Marijus /etc/init.d/mysql[6490]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Nov  6 12:13:17 FrontIT-Marijus /etc/init.d/mysql[6490]: 
```

**/media/Data** is one of my NTFS drives shared between OSes (auto)mounted with 777 permissions
**/media/Data/MySQL/Datafiles/** is mysql data_dir (in /etc/mysql/my.cnf)

The problem with permissions was actually hiding in AppArmor. Adding the following line to /etc/apparmor.d/usr.sbin.mysqld fixed it:
```
  /media/Data/MySQL/** rwk,
```
I've added it just below the other paths (note, that **/var/lib/mysql/**, which is default data_dir, has the same permissions)

Finally
```
sudo /etc/init.d/apparmor restart
sudo /etc/init.d/mysql restart
```

Hope this helps someone ;)

---

