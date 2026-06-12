---
title: "Hdparm doesn't read hard disk cache size"
date: 2015-08-26
forum: Hardware
---

### Post by cogset on 2015-08-26
I'm using hdparm to read the characteristics  of my WD blue hard disk, it is supposed to have a 64MB cache, however the output of **hdparm -I** looks like that ```
cache/buffer size  = unknown
```whilst **hdparm -i** says```
 BuffType=unknown, BuffSize=0kB
```
in short looks like it just can't access such data on this particular drive.
It works however with other SATA drives from other manufacturers that I have, so why it doesn't with this WD unit ?

---

### Post by dino99 on 2015-08-26
what says the boot mog, or dmesg/syslog/journalctl ?
you can run lshw too and/or lspci

---

### Post by cogset on 2015-08-27
I can't see no info about the hard disk cache in any of these... maybe I just  don't know where to look, but neither in the logs or the output of lshw and lspci I can see such info. 

 Is hdparm the only specific tool in this field ? 

 I've  tried in different OSes and it just can't read the cache size of this WD disk: is this an issue with hdparm, or maybe there's something peculiar with such drives?

---

### Post by efflandt on 2015-08-27
I forget if I have a black or blue 1 TB WD drive (that replaced failed Seagate), but same results as you for that or Intel 80 GB SSD in 64-bit 14.04. And dmesg or sudo lshw do not show any drive buffer or cache info.

---

