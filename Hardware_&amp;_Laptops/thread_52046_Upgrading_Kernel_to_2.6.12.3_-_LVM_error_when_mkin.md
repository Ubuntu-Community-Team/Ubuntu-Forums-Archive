---
title: "Upgrading Kernel to 2.6.12.3 - LVM error when mkinitrd"
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by jeyno on 2005-07-26
Hi folks,

Been scouring all earthly newsgroups and lists for help on this issue.  Time to make a post of my own.

Running Ubunto Hoary 5.04 on a laptop where filesystems are configured as follows:

[FONT=Lucida Console]
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/VolGroup00-LogVol00 /               reiserfs defaults        0  1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
[/FONT]

when I come to mkinitrd I get the following noise...

[FONT=Lucida Console]
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
File descriptor 7 left open
    Finding all volume groups
    Finding volume group "VolGroup00"
/usr/sbin/mkinitrd: /dev/mapper/VolGroup00-LogVol00: Kernel does not support 
[/FONT]

There is a collection of posting on the Web relating to debian users experiencing similar trauma.  Can anyone help me understand what's going on here?

btw, my new kernel jolly well should support LVM... the relevant section from my .config is as shown here

[FONT=Lucida Console]
#
# Multi-device support (RAID and LVM)
#
CONFIG_MD=y
CONFIG_BLK_DEV_MD=y
CONFIG_MD_LINEAR=m
CONFIG_MD_RAID0=m
CONFIG_MD_RAID1=y
CONFIG_MD_RAID10=m
CONFIG_MD_RAID5=m
CONFIG_MD_RAID6=m
CONFIG_MD_MULTIPATH=m
CONFIG_MD_FAULTY=m
CONFIG_BLK_DEV_DM=y
# CONFIG_DM_CRYPT is not set
# CONFIG_DM_SNAPSHOT is not set
# CONFIG_DM_MIRROR is not set
# CONFIG_DM_ZERO is not set
# CONFIG_DM_MULTIPATH is not set
[/FONT]

---

