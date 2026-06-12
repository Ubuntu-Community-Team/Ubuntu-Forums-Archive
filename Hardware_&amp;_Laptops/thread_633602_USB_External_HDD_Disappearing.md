---
title: "USB External HDD Disappearing"
date: 2007-12-06
forum: Hardware &amp; Laptops
---

### Post by TornMorals on 2007-12-06
Hey guys!
Well having a of trouble righting to my external hard drive.   The model is a Maxtor Personal Storage 3100.  It is a standard internal hard drive with a USB converter I have found. (Couldn't resist the urge to open it and check.  After all if you cant open it you don't know it. XD)
In the past it has worked fine but I had never actually tried to copy data to it from Linux.  Data reads fine.  And the only time I have copied anything it was < 3GB.

Now that I'm trying to copy a large amount of data it keeps dropping while transferring resulting in an I/O Error while trying to do so and partial file transfers. 
Any ideas on finding what it is doing and fixing it.  Ubuntu 7.04 (Need to backup before upgrade).

Thanks
TM

---

### Post by markp1989 on 2007-12-06
i get the same thing, with gusty when trying to back up my music

---

### Post by taurus on 2007-12-06
What's the output of this command from a terminal with your external drive plugged in and on?

```
sudo fdisk -l
```

---

### Post by TornMorals on 2007-12-07
```

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19123   153600000    7  HPFS/NTFS
/dev/sda2           30142       30515     3004155   82  Linux swap / Solaris
/dev/sda3           19124       30141    88502085   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6375    51200000   83  Linux
/dev/sdb2            6375       30516   193913856    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321   83  Linux

```

/dev/sdc is the external HDD.

---

