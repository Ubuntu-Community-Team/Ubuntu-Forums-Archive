---
title: "can't mount usb drive"
date: 2013-12-18
forum: Hardware
---

### Post by irgendwer99 on 2013-12-18
Hi for everybody!
Perhaps can help me somebody:
I bought a new 3 TB Toshiba drive, conected it to my laptop(ubuntu) and my desktop(ubuntu) copied a lot of file to the drive.
Then I conected it to my ubuntu server ( 12.04.3).
I mounted it and copied, deleted files (remotely). Everything was ok. I didn't umounted it. The next day - when I wanted to mount I received the following message:

xxx@ubuntu:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/external
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

The same did work a day before...

Something more to the problem:

xxx@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006627c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   312580095   156039169    5  Extended
/dev/sda5          501760   312580095   156039168   8e  Linux LVM

Disk /dev/mapper/ubuntu--vg-root: 158.8 GB, 158842486784 bytes
255 heads, 63 sectors/track, 19311 cylinders, total 310239232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/sdb: 3000.6 GB, 3000592977920 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x027b96bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         256   732566271   366283008    7  HPFS/NTFS/exFAT

Disk /dev/mapper/ubuntu--vg-swap_1: 939 MB, 939524096 bytes
255 heads, 63 sectors/track, 114 cylinders, total 1835008 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

Please help!

---

### Post by tfrue on 2013-12-20
Have you tried to connect it to you laptop or desktop to see if it would mount auto magically?

---

