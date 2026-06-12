---
title: "Unable to install MySQL"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by absk on 2009-07-27
I have just moved from Windows and am unable to install MySQL

I installed lamp using apt-get but it could not install completely. I read somewhere that I should run
 ```
sudo apt-get -f install
```
Now i am getting this, same as before:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfreebob0 libwildmidi0 libsoundtouch1c2 libjack0 libopenspc0 libcdaudio1
  libmpcdec3 libmms0 libiptcdata0 libfaad0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 298 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.4) ...
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
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have no idea what to do.

---

