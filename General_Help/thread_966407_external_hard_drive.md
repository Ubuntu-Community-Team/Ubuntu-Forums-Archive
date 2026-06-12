---
title: "external hard drive"
date: 2008-11-01
forum: General Help
---

### Post by hndaklr8480 on 2008-11-01
hi again folks.  I was given 250g external hard drive(awsome) but my linux box doesnt mount to desktop.  

output of sudo fdisk -l :

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x42b8e0c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9545    76670181   83  Linux
/dev/sda2            9546        9729     1477980    5  Extended
/dev/sda5            9546        9729     1477948+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059349504 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa919a919

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1023     8217243   54  OnTrackDM6


so it sees it here how to i mount to desk top if i plug in to vista box it automatically loaded driver and was accessible but i want to use it with ubuntu not vista. thanx for any help

---

