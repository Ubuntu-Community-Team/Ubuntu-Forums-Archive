---
title: "FAT32 partition for data and swap??"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by superpollo on 2009-09-26
hello, i'm having a problem, when i installed ubuntu 9.04 on the partition manager i put the swap file on my data partition, can i resolve this without reinstalling ubuntu???

here are the results of terminal:

fdisk
a@a-laptop:/tmp/tmpEpxtqz$ [COLOR="Red"]fdisk[/COLOR]

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

sudo fdisk -l

julioaquino@julioaquino-laptop:/tmp/tmpEpxtqz$ sudo fdisk -l
[sudo] password for julioaquino: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92e02cb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1402    11261533+   7  HPFS/NTFS
/dev/sda2            4621       14579    79995667+   f  W95 Ext'd (LBA)
/dev/sda3            1403        4620    25848585   83  Linux
/dev/sda5            4621       14579    79995636   82  Linux swap / Solaris

Partition table entries are not in disk order

cat /etc/fstab

julioaquino@julioaquino-laptop:/tmp/tmpEpxtqz$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=0d3f8dd1-dc86-4a4b-9a51-406b1ccca1aa /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=81bad9de-987f-4638-8d6b-6176c449ae6d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sudo blkid
julioaquino@julioaquino-laptop:/tmp/tmpEpxtqz$ sudo blkid
/dev/sda1: UUID="AE9CBE589CBE1B33" TYPE="ntfs" 
/dev/sda3: UUID="0d3f8dd1-dc86-4a4b-9a51-406b1ccca1aa" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="81bad9de-987f-4638-8d6b-6176c449ae6d" 


thanks

---

### Post by oldfred on 2009-09-26
Is it really in your data partition or just in a large extended partition? Using a liveCD and gparted you can edit the partitions. You may have to turn swapoff. Normally swap is put into an extended partition so it does not use one of the 3 remaining primary partitions.
If you delete your swap you will have to update the UUID entry in your fstab. If you cannot move it then you can delete it and put it somewhere else.

---

