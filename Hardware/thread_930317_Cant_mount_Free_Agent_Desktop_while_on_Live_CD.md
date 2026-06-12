---
title: "Cant mount Free Agent Desktop while on Live CD"
date: 2008-09-25
forum: Hardware
---

### Post by nonpareil on 2008-09-25
Hi,
I'm new to ubuntu and was on XP till now. I used XP and I have loads of data on my laptop, so I was hoping to use the live CD to boot ubuntu 8.04, attach my Free Agent Desktop 500GB drive and save my data before formatting the drive to install ubuntu 8.04.
Problem is, I cant mount my external hard drive. I also enabled and installed the ntfs-3g since my free agent is ntfs formatted. it was working fine with XP but I want to save data before I try installing ubuntu8.04.
I have 2 questions. 
1. Can we access free agent drives while on live cd? 
2. If i do go ahead and install, will I lose all data since my laptop isn't partitioned right now?
here are some commands and outputs i got.
Any ideas what I'm missing here??

ubuntu@ubuntu:/$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        6755    54203310    7  HPFS/NTFS
/dev/sda3            6756        7295     4337550   db  CP/M / CTOS / ...

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x33cf33ce

   Device Boot      Start         End      Blocks   Id  System
ubuntu@ubuntu:/$ sudo mount -t ntfs-3g /dev/sdc /media/external -o force
NTFS signature is missing.
Failed to mount '/dev/sdc': Invalid argument
The device '/dev/sdc' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

~Nonpareil

---

