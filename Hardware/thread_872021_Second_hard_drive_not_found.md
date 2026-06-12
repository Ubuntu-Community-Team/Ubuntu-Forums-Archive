---
title: "Second hard drive not found"
date: 2008-07-27
forum: Hardware
---

### Post by quantum_mechanik on 2008-07-27
Hi. I'm completely 100% new to uBuntu, and I've a bit of a problem.

I installed it on my Acer Aspire 9410, as a dual-boot thing, and now I can't find my second hard drive--the one with all my media on it. Is there any way to search for it? It's the e:\

---

### Post by cariboo on 2008-07-27
Hard drives do not have drive letters in Linux. Your hard drive will be called something like /dev/sda1, To find your hard drive in a Applications-->Accessories-->Terminal type:

```
sudo fdisk -l
```

This will print a list of the hard drives connected to your computer. If you could paste the output of the above command in your next post, we can help you access your hard drive.

Jim

---

### Post by silkstone on 2008-07-27
You seem to have posted twice about the same thing...

[http://ubuntuforums.org/showthread.php?p=5470063#post5470063](http://ubuntuforums.org/showthread.php?p=5470063#post5470063)

---

### Post by quantum_mechanik on 2008-07-27
> **cariboo907 said:**
> Hard drives do not have drive letters in Linux. Your hard drive will be called something like /dev/sda1, To find your hard drive in a Applications-->Accessories-->Terminal type:

```
sudo fdisk -l
```

This will print a list of the hard drives connected to your computer. If you could paste the output of the above command in your next post, we can help you access your hard drive.

Jim

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbdfbbdfb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1020     8193118+  27  Unknown
/dev/sda2   *        1021        7807    54516577+   7  HPFS/NTFS
/dev/sda3            7808       14593    54508545    7  HPFS/NTFS

Disk /dev/mmcblk0: 1021 MB, 1021313024 bytes
15 heads, 46 sectors/track, 2890 cylinders
Units = cylinders of 690 * 512 = 353280 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1        2891      997252+   6  FAT16

---

### Post by quantum_mechanik on 2008-07-27
> **silkstone said:**
> You seem to have posted twice about the same thing...

[http://ubuntuforums.org/showthread.php?p=5470063#post5470063](http://ubuntuforums.org/showthread.php?p=5470063#post5470063)

Sorry. Wasn't sure where to put it.

---

