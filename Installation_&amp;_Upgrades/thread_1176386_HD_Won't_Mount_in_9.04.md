---
title: "HD Won't Mount in 9.04"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by Rayn on 2009-06-02
Just did a fresh install of Mythbuntu 9.04.  Previously was using 8.04 and things were working just fine.  I have 2 of the same hard drive but one mounts, the other will not.  Here is all the relevant information I can find, is there anyway to restore my drive?

 mount -t ext3 /dev/sda /var/lib/mythtv/videos/VHD2
> 
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


dmesg | tail
> [  153.132791] VFS: Can't find an ext2 filesystem on dev sda.
[  160.728066] VFS: Can't find ext4 filesystem on dev sda.
[  164.738320] VFS: Can't find ext3 filesystem on dev sda.


fstab
> 
/dev/sda        /var/lib/mythtv/videos/VHD2     ext3    defaults        0      $
/dev/sdb        /var/lib/mythtv/videos/VHD3     ext3    defaults        0      $


fdisk -l
> 
fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d3832

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1459    11719386   83  Linux
/dev/sdc2            1460      121601   965040615    5  Extended
/dev/sdc5            1460        1583      995998+  82  Linux swap / Solaris
/dev/sdc6            1584      121601   964044553+  83  Linux
(As a side note, why does sdb not contain a valid partition table but still work just fine?)

 ls /dev/sd*
> /dev/sda  /dev/sdb  /dev/sdc  /dev/sdc1  /dev/sdc2  /dev/sdc5  /dev/sdc6

ls /var/lib/mythtv/videos/VHD3 (working)
> lost+found  Movies  old

Any and all feedback is appreciated, I have no experience with hard drive issues like this so far.

---

### Post by MichaelSammels on 2009-06-02
First of all, try installing Storage Device Manager:

```
sudo apt-get install pysdm
```
```
sudo pysdm
```

If you suspect your partition table to be corrupt, but works fine, I would leave it until starts to cause serious problems.

---

### Post by Rayn on 2009-06-02
I won't be messing with the working disk, was just a sidebar question regarding the working disk (/dev/sdb)

---

