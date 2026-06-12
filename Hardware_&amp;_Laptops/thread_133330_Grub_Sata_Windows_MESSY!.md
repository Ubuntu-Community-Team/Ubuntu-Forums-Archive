---
title: "Grub Sata Windows MESSY!"
date: 2006-02-20
forum: Hardware &amp; Laptops
---

### Post by Trab on 2006-02-20
alright, so i have had some weird issues with my machine, finally fixed em all up...
now i have a restored windows partion on my /dev/hda1 drive (a copy is on /dev/sda1, but that wont boot)

so i need to know wat to set the grub menu to to get it to boot...
ive tired 
(hd1,0)
(hd0,0)
ubuntu boots from (hd0,1) (also know as /dev/sda2)
so where would /dev/hda1 be?
thanks
-Trab

---

### Post by Sutekh on 2006-02-20
Have a look inside ```
sudo gedit /boot/grub/device.map
```
and look at the output of ```
sudo fdisk -l
```

Here's mine```

(hd0)   /dev/hda
(hd1)   /dev/sda
(hd2)   /dev/sdb
```
```
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       14593   117218241    5  Extended
/dev/hda5               1       14593   117218209+   b  W95 FAT32

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24320   195350368+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2432    19535008+  83  Linux
/dev/sdb2            2433       30401   224660992+   5  Extended
/dev/sdb5           30024       30401     3036253+  82  Linux swap / Solaris
/dev/sdb6            2433        9727    58597024+  83  Linux
/dev/sdb7            9728       26979   138576658+  83  Linux

Partition table entries are not in disk order

```

 - Remember to start counting partitions from 0.

 - For me Windows boots from /dev/sda1 -> (hd1,0)

 - Ubuntu boots from /dev/sdb1 -> (hd2,0)

---

