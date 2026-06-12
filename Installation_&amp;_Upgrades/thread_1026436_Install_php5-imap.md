---
title: "Install php5-imap"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by bellalamb on 2008-12-31
Hi - Having trouble installing php5-imap

7.04 server

I get the following errors 

```

login as: paul
paul@192.168.7.18's password:
Linux ubuntu2 2.6.20-15-server #2 SMP Sun Apr 15 07:41:34 UTC 2007 i686


Last login: Wed Dec 31 09:20:03 2008
paul@ubuntu2:~$ sudo apt-get install php5-imap
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libc-client2002edebian mlock
Suggested packages:
  uw-mailutils
The following NEW packages will be installed
  libc-client2002edebian mlock php5-imap
0 upgraded, 3 newly installed, 0 to remove and 40 not upgraded.
Need to get 677kB of archives.
After unpacking 1479kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  mlock libc-client2002edebian php5-imap
Install these packages without verification [y/N]? y
Err http://gb.archive.ubuntu.com feisty/universe mlock 7:2002edebian1-13.1ubuntu1
  404 Not Found
Err http://gb.archive.ubuntu.com feisty/universe libc-client2002edebian 7:2002edebian1-13.1ubuntu1
  404 Not Found
Err http://gb.archive.ubuntu.com feisty/universe php5-imap 5.1.2-1ubuntu1
  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/u/uw-imap/mlock_2002edebian1-13.1ubuntu1_i386.deb  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/u/uw-imap/libc-client2002edebian_2002edebian1-13.1ubuntu1_i386.deb  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/p/php-imap/php5-imap_5.1.2-1ubuntu1_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
paul@ubuntu2:~$


```

---

