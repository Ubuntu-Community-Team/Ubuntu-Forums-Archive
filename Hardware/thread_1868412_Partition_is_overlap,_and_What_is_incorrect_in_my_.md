---
title: "Partition is overlap, and What is incorrect in my partition?"
date: 2011-10-24
forum: Hardware
---

### Post by bluekyu on 2011-10-24
[FONT=Arial]I tried to install ubuntu newly. But partition tool did not detect my original partition.
In parted, it said Error: Can't have overlapping partitions.

So I checked my partition with fdisk and sfdisk, and I tried to resolve this problem.
(I referred to [http://ubuntuforums.org/showthread.php?t=1072331](http://ubuntuforums.org/showthread.php?t=1072331) and 
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598))
But I don't know what incorrect is in my partition. Where is incorrect?

Thank you.

< fdisk -l >
[/FONT]```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbab21f87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2932    23551258+   7  HPFS/NTFS
/dev/sda2            2933        7469    36443452+  83  Linux
/dev/sda3            7470       38913   252567393+   5  Extended
/dev/sda4            7470       13045    44775424   83  Linux
/dev/sda5           13045       18025    40000083+  83  Linux
/dev/sda6           18025       18522     4000153   82  Linux swap / Solaris
/dev/sda7           18523       28248    78124063+  83  Linux
/dev/sda8           28249       38913    85666581   83  Linux
```[FONT=Arial]

< fdisk -lu >
[/FONT]```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbab21f87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    47102579    23551258+   7  HPFS/NTFS
/dev/sda2        47102580   119989484    36443452+  83  Linux
/dev/sda3       120002558   625137344   252567393+   5  Extended
/dev/sda4       120002560   209553407    44775424   83  Linux
/dev/sda5       209555456   289555622    40000083+  83  Linux
/dev/sda6       289555624   297555929     4000153   82  Linux swap / Solaris
/dev/sda7       297555993   453804119    78124063+  83  Linux
/dev/sda8       453804183   625137344    85666581   83  Linux
```[FONT=Arial]

< sfdisk -d >
[/FONT]```
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 47102517, Id= 7, bootable
/dev/sda2 : start= 47102580, size= 72886905, Id=83
/dev/sda3 : start=120002558, size=505134787, Id= 5
/dev/sda4 : start=120002560, size= 89550848, Id=83
/dev/sda5 : start=209555456, size= 80000167, Id=83
/dev/sda6 : start=289555624, size=  8000306, Id=82
/dev/sda7 : start=297555993, size=156248127, Id=83
/dev/sda8 : start=453804183, size=171333162, Id=83
```[FONT=Arial]

<sfdisk -V >
[/FONT]```
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: partition 3 does not start at a cylinder boundary
```[FONT=Arial]
[/FONT]

---

