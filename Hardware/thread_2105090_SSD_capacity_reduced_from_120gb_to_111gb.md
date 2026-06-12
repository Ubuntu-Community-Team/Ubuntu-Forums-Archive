---
title: "SSD capacity reduced from 120gb to 111gb"
date: 2013-01-15
forum: Hardware
---

### Post by Famedoro on 2013-01-15
Hi all.
I have a Samsung ssd 128 gb, then counting every KB equals 1024 B I calculated an exact capacity of 119gb.
Installing Ubuntu 12.04 on the SSD, the installer recognize  a space of 120gb (in line with my predictions of 119gb).
When I try to overwrite Windows, however, the space is reduced to 111gb, losing 8-9 gb. No other partition detected.
I tried a live of Ubuntu from USB and then use Gparted.
Gparted finds 111 gb of free space and does not detect any other partition.
I tried to run the installer of Ubuntu to recheck how many gb were available and they magically come back to be 120.
Have you some idea?

---

### Post by Grenage on 2013-01-15
EXT keeps 5% of the system as emergency store, for the use of root.  You can change the amount it reserves, or disable it (I believe).  Here's another explanation:

[http://boncey.org/2006_11_18_reclaiming_ext3_disk_space](http://boncey.org/2006_11_18_reclaiming_ext3_disk_space)

---

