---
title: "mouting external hard drive"
date: 2009-01-11
forum: Hardware
---

### Post by razzle82 on 2009-01-11
I'm trying to mount my external hard drive but i'm not sure what am i doing wrong. i also downloaded NTFS configuration tool that did work but not any more.

thank you in advance

---

### Post by taurus on 2009-01-11
Did you "safely remove" the external harddrive the last time you used it?  Or did you just unplug it?

Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by razzle82 on 2009-01-12
i did that and here what came up

faraz@faraz-desktop:~$ sudo fdisk -l
[sudo] password for faraz: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4681    37600101   83  Linux
/dev/sda2            4682        4865     1477980    5  Extended
/dev/sda5            4682        4865     1477948+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       16708   134206978+   7  HPFS/NTFS
faraz@faraz-desktop:~$

---

