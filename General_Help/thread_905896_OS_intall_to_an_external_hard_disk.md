---
title: "OS intall to an external hard disk"
date: 2008-08-30
forum: General Help
---

### Post by ajay2589 on 2008-08-30
hii all

i have a few doubts regarding installation of ubuntu onto an external hard disk....! i've listed out them...! please try to solve...

i have a laptop, in which the OS is windows vista...i have an external hard disk of 250gb..... i made a partition and installed xp into one.... and again created another partition and installed ubuntu ultimate onto it.... 

1) i dont understand the hd1 and hd0 notations given for the GRUB installation..

then... after the installation, the windows xp doesnt boot.... the err shown is hal.dll is removed or corrupted.... i can understand that hal.dll is the ardware abstraction layer....

2) how can i recover my windows xp....?? and keep two or more OS(win xp and a few versions of linux) in external hard disk and boot from it....

please help

thanq

---

### Post by Joeb454 on 2008-08-30
Moved to General Help :)

---

### Post by cdtech on 2008-08-30
Examples of the difference from the GNU/Linux and GRUB device names:

**1st Physical Hard Drive:**
Linux IDE: GRUB IDE: Linux SCSI: GRUB SCSI:
/dev/hda1 ----(hd0,0)----- /dev/sda1-------(hd0,0)
/dev/hda2 ----(hd0,1)----- /dev/sda2-------(hd0,1)
/dev/hda3 ----(hd0,2)----- /dev/sda1-------(hd0,2)
/dev/hda4 ----(hd0,3)------/dev/sda2-------(hd0,3)

**2nd Physical Hard Drive:**
Linux IDE: GRUB IDE: Linux SCSI: GRUB SCSI:
/dev/hdb1---- (hd1,0)----- /dev/sdb1------ (hd1,0)
/dev/hdb2---- (hd1,1)----- /dev/sdb2------ (hd1,1)
/dev/hdb3---- (hd1,2)----- /dev/sdb1------ (hd1,2)
/dev/hdb4---- (hd1,3)----- /dev/sdb2-------(hd1,3)

---

### Post by ajay2589 on 2008-08-30
i've got an internal hard disk of 160GB SATA inside my laptop and a USB hard drive of 250GB SATA connected externally.....!

pls specify which will be my hd1 and hd0.......?? can u predict it as such......??

---

### Post by cdtech on 2008-08-30
You would need to open a terminal and type:
```
sudo fdisk -l
```
The output will look as mine does below:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000116f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         191     1534176   83  Linux
/dev/sda2             192       16454   130632547+   5  Extended
/dev/sda3           16455       30401   112029277+   7  HPFS/NTFS
/dev/sda5             192         447     2056288+  82  Linux swap / Solaris
/dev/sda6             448        8803    67119538+  83  Linux
/dev/sda7            8804       16454    61456626   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f29dfaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18359   147468636    7  HPFS/NTFS
/dev/sdb2           18360       19457     8819685    7  HPFS/NTFS

Disk /dev/**sdc**: 1024 MB, 1024966656 bytes
255 heads, 63 sectors/track, 124 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002fee2

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdc1               1         124      995998+  83  Linux**

```
You can see my external USB is listed as /dev/**sdc**

---

