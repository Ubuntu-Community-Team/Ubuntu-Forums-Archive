---
title: "External HD permission woes"
date: 2006-06-29
forum: Hardware &amp; Laptops
---

### Post by MBro on 2006-06-29
I just bought a [400gb Hard drive for $109]("http://shop3.outpost.com/product/4596287?site=sr:SEARCH:MAIN_RSLT_PG") and then threw it in an external case.  I connected it to my computer, formatted it as ext3.  It mounted itself automaticly as usbdisk but I have a problem.  Only root can write to it.  I checked my users/groups settings and my user name is in the plugdev group.  I tried changing the permissions as root to from within nautilus but had no luck.  Any ideas?

---

### Post by aysiu on 2006-06-29
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by V0oD0oman on 2006-06-29
[QUOTE=aysiu][http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)[/QUOTE]

I used this tutorial to try and mount two jfs harddrives and when i did "sudo mount -a" i got the following error

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


I checked gparted for the filesystem type, and it is jfs (i knew this prior anyways).  basically what happened is that the power cables for the computer fell out during the upgrade to dapper, and now i am left with 2 drives i cannot access out of my raid.  We have 6 drives, each mirrored so there is the prime drive with the OS, that is running JFS and working ok.  The other two drives are also JFS and will not mount.  Any suggestions?

---

### Post by MBro on 2006-06-30
So it seems that all it took was a nice reboot to get the permissions working correctly.  Sorry that I can't help with your problem voodooman.

---

