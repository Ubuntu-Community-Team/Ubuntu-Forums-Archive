---
title: "seeking assistance w install ...grub?"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by hit1mn on 2009-05-05
hi all,

i have been working w a 9.04 install up until a couple days ago. everything was working well and had been testing a bunch of apps in vm's then installing locally. 

after a handful of reloads I created a hd image w clonezilla (updated ver, not jaunty ver)


A couple days ago I hosed up my local install and reloaded the image

see [http://ubuntuforums.org/showthread.php?t=1148368](http://ubuntuforums.org/showthread.php?t=1148368)

After trying to install grub every which way I could find I ended up zeroing the drive in an attempt to validate it's integrity w 
[FONT=Verdana]dd if=/dev/zero of=/dev/TARGETDRIVE bs=1M[/FONT]

[FONT=Verdana]This completed after several hrs on a 500gb sata. 

Then reloaded the clone image. Same result

Zeroed the disk again overnight and now am not able to complete a simple local install.

The installed had failed (hung) at 2 diff spots..33% and 83%

Any suggestions?

MB BIOSTAR TFORCE TA790GX 128M RT
CPU AMD|PH X4 9950 BLK2.6G 65N R
MEM 2Gx4|OCZ OCZ2G8008GQ R (8GB total)
WinTV-HVR-1800 (CX23385/7 driver)
SATA HD 1T|WD 32M WD10EADS (2ea)(Green)
SATA HD 500GB WD (1ea) Blue
DVD BURN SAMSUNG|SH-S223Q LS
2.6.28-11-server w/GUI

Thanks
[/FONT]

---

### Post by hit1mn on 2009-05-05
back to a blinking cursor. 

One the 3rd try my install completed. Took all defaults except did not use lvm

I'm hoping this means my clonezilla image is good

---

### Post by hit1mn on 2009-05-05
ubuntu@ubuntu:/dev$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000402ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       58336   468583888+  83  Linux
/dev/sda2           58337       60801    19800112+   5  Extended
/dev/sda5           58337       60801    19800081   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002e48d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ab931

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      118653   953080191   83  Linux
/dev/sdc2          118654      121601    23679810    5  Extended
/dev/sdc5          118654      121601    23679778+  82  Linux swap / Solaris
ubuntu@ubuntu:/dev$ 


anyone with a suggestion?

---

### Post by dstew on 2009-05-05
What is your problem at present? You say you completed the installation. Are you able to boot that installation?

---

### Post by hit1mn on 2009-05-05
I figured I would be but no. Still have blinking cursor

thanks

---

### Post by dstew on 2009-05-05
Do you get any grub messages at all? After BIOS accesses the disk, what happens?

---

### Post by hit1mn on 2009-05-06
here is some updated output after the local install. I'm not sure why anything would change though....

after rebooting and the bios splash screen it just drops to a blinking cursor, no grub msgs

grub> find /boot/grub/stage1
 (hd0,0)
 
grub> root  (hd0,0)
 
grub> setup  (hd0,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.
 
grub> geometry (hd0)
drive 0x80: C/H/S = 60801/255/63, The number of sectors = 976773168, /dev/sda
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82
 
grub> geometry (hd1)
drive 0x81: C/H/S = 121601/255/63, The number of sectors = 1953525168, /dev/sdb
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
 
grub> geometry (hd2)
drive 0x82: C/H/S = 121601/255/63, The number of sectors = 1953525168, /dev/sdc
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
 
grub>

---

### Post by dstew on 2009-05-07
The behavior you have is consistent with your BIOS loading what it thinks is a boot loader from the hard disk it thinks is the boot disk, but the "boot loader" is non-functional, or just random bytes, which would be the case if the disk had recently been zeroed.

In looking at your grub re-install, I note you did **setup (hd0,0)**. This would cause the grub boot loader to go into the first sector of the first partition on (hd0). I think what you really want is the boot loader to go into the Master Boot Record (MBR) of (hd0). If that is what you want, you need to do```
root (hd0,0)
setup (hd0)
```
The MBR is not a part of any partition. Some BIOSes can boot a partition, but most will need a boot loader in the MBR.

---

