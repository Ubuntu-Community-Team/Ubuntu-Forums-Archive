---
title: "HDD problem"
date: 2013-12-24
forum: Hardware
---

### Post by tanatos84 on 2013-12-24
Hi, my problem is probably with a bad GPT, my problem started when I tried to setup a GPT on my hdd it was succesful but after that the hdd shows aanly 4 GB instead of 4TB,by the way the hdd is a seagate of 4tb is a recent purchase so it maight have a factory error.
if I run gdisk /dev/sda  I receive in return:

Warning! Read error 5; strange behavior now likely!
Warning! Read error 5; strange behavior now likely!
Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.

if I run fixpart /dev/sda I got:

Loading MBR data from /dev/sda
Problem opening /dev/sda for reading! Error is 13.
You must run this program as root or use sudo!

Unable to read MBR data from '/dev/sda'! Exiting!


I try hiren boot disk and noting helps.


please help me.

---

### Post by tanatos84 on 2013-12-24
[update]

sudo fdisk -l

returns:

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf950bad9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   125042687    62520320    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 7803 MB, 7803174912 bytes
241 heads, 62 sectors/track, 1019 cylinders, total 15240576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?  3224498923  3657370039   216435558+   7  HPFS/NTFS/exFAT
/dev/sdc2   ?  3272020941  5225480974   976730017   16  Hidden FAT16
/dev/sdc3   ?           0           0           0   6f  Unknown
/dev/sdc4        50200576   974536369   462167897    0  Empty

Partition table entries are not in disk order



sdb is an ssd and it's ok. sdc is a usb stick the rest is for the 4tb disk.

---

