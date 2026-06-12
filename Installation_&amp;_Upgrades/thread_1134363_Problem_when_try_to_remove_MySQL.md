---
title: "Problem when try to remove MySQL"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by gjhames on 2009-04-23
[FONT=Courier New][FONT=Verdana]Hi, I'm trying to remove mysql from my machine. Ubuntu 8.4 AMD64.
**after exec this command: **
[FONT=Courier New]sudo aptitude --purge remove mysql-server-5.0 mysql-server[/FONT]
**I have this output**
[/FONT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x php5-common php5-gd 
The following packages have been kept back:
  apt-utils cupsys cupsys-bsd cupsys-client cupsys-common firefox firefox-3.0 firefox-3.0-gnome-support firefox-gnome-support ghostscript ghostscript-x gvfs gvfs-backends 
  gvfs-fuse libapache2-mod-php5 libcupsimage2 libcupsys2 libgs8 libgvfscommon0 libpoppler-glib2 libpoppler2 libvolume-id0 php5-mysql php5-pgsql poppler-utils tasksel 
  tasksel-data tzdata udev xfonts-scalable xulrunner-1.9 xulrunner-1.9-gnome-support 
The following packages will be REMOVED:
  mysql-server-5.0 
0 packages upgraded, 0 newly installed, 1 to remove and 41 not upgraded.
Need to get 0B of archives. After unpacking 89.2MB will be freed.
Writing extended state information... Done
(Reading database ... 217962 files and directories currently installed.)
Removing mysql-server-5.0 ...
 * Stopping MySQL database server mysqld                                                                                                                                  [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing mysql-server-5.0 (--remove):
 subprocess pre-removal script returned error exit status 1
 * Stopping MySQL database server mysqld                                                                                                                                  [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MySQL database server mysqld                                                                                                                                  [ OK ] 
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done[/FONT]

And mysql seems don't want to be removed.

---

### Post by mwacky on 2009-04-23
It looks like Mysql will not fully stop.  Try to stop mysql before running the purge.  You could disable from starting at bootup then reboot and try the operation again.

---

### Post by gjhames on 2009-04-23
yes, if I try to stop the mysql daemon before execute this command, I receive the output that the deamon was stoped:
/etc/init.d/mysql stop

---

