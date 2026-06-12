---
title: "really bad install, need low level fixing"
date: 2008-09-19
forum: General Help
---

### Post by DiGiTY on 2008-09-19
i tried an alternative way of installing netatalk (so I could enable encrypted authenication) and I ended up mucking something up in aptitude to the point I can't install nor remove netatalk.

I get the following when trying to remove it:

```

digity@baushaus:/$ sudo apt-get remove netatalk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  netatalk
0 upgraded, 0 newly installed, 1 to remove and 31 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 2142kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing netatalk (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 netatalk
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

And when I try to re-install netatalk I get the following error:

```
digity@baushaus:/$ sudo apt-get -f install netatalk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  tetex-bin quota timeout
Recommended packages:
  rc slpd db4.2-util
The following packages will be upgraded:
  netatalk
1 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.
1 not fully installed or removed.
Need to get 0B/717kB of archives.
After unpacking 160kB disk space will be freed.
Selecting previously deselected package netatalk.
(Reading database ... 153924 files and directories currently installed.)
Preparing to replace netatalk 2.0.3-6ubuntu1 (using .../netatalk_2.0.3-6ubuntu1_i386.deb) ...
hostname: Unknown host
invoke-rc.d: initscript netatalk, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
hostname: Unknown host
invoke-rc.d: initscript netatalk, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/netatalk_2.0.3-6ubuntu1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
hostname: Unknown host
invoke-rc.d: initscript netatalk, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/netatalk_2.0.3-6ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

any ideas?

---

### Post by andrewc6l on 2008-09-19
I would try:
sudo rm /var/cache/apt/archives/netatalk_2.0.3-6ubuntu1_i386.deb
sudo aptitude update
sudo aptitude reinstall netatalk

and if that doesn't work, try dpkg... but something strange is going on with the install script for netatalk. Is your hostname set properly? You're getting:
hostname: Unknown host

You might want to look into that. Make sure you get the right values for hostname -f and hostname -i as well as hostname. More details are here:
[http://ubuntuforums.org/showthread.php?t=313576](http://ubuntuforums.org/showthread.php?t=313576)

---

