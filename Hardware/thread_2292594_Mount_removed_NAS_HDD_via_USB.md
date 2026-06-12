---
title: "Mount removed NAS HDD via USB?"
date: 2015-08-29
forum: Hardware
---

### Post by david427 on 2015-08-29
Hi there,

I have removed the HDD from a NAS device and am looking to mount the drive so I can remove the files from it.

Initially when i first connected it to the ubuntu machine it found it no problem but now it does not. There are other partitions that appear but the data i'm interested does not. This is a 2TB WD drive.

Any idea how i go about mounting this drive so I can transfer my data?


david@david-laptop:~$ sudo gdisk /dev/sdb
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): ^Cdavid@david-laptop:~$ 
david@david-laptop:~$ blkid
david@david-laptop:~$ sudo blkid /dev/sdb
david@david-laptop:~$ sudo blkid
/dev/sda1: LABEL="ACER" UUID="320D-180E" TYPE="vfat" 
/dev/sda5: UUID="677b6fc7-84de-4b73-a996-340bb4847164" TYPE="ext4" 
/dev/sda6: UUID="4c0a6f72-9440-4f2a-836c-801e75dbd014" TYPE="swap" 
/dev/sdb1: UUID="a6f8e76b-e215-441e-82ca-bb0c8c6a1631" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="cdaf4f12-96b1-45fa-97dd-8cb6a99e013c" TYPE="ext3" 
/dev/sdb5: TYPE="swap"

---

### Post by TheFu on 2015-08-30
Some NAS devices use proprietary formats. Most have a "forum" which explain the partition layout and how to mount those partitions when there is a failure.

Be careful using gdisk.  Try posting **sudo parted -l**. and **sudo lsblk** output - please use code tags so things line up.

---

