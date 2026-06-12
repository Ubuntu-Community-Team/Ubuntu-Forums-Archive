---
title: "External USB Drive  no longer mounts after Unclean Shutdown"
date: 2009-09-09
forum: Hardware
---

### Post by Levitation on 2009-09-09
Please Help!

I was trying to install an Ubuntu boot on my USB Drive (320GB Maxtor) using USB Startup Disk Creator.

It asked me if I wanted to format the drive and without thinking I hit YES. I panicked when I realized it would erase all of the data on my drive so I unplugged the usb cable from the drive (I know... bad idea).

When I plugged the drive back in, it was not recognized.

So then:

sudo fdisk -l

Device Boot     Start     End        Blocks                 Id     System
/dev/sdb1                 1    38914    312571223+       c     W95  FAT32 (LBA)

Tried to mount (and force mount) in terminal and this is what I got:

wrong fs type, bad option, bad superblock on /dev/sdb1, 
missing codepage or helper program, or other error
In some cases useful info is found in syslog  -  try
dmesg | tail   or so

Partial Output of   dmesg | tail

FAT: Unrecognized mount option "force" or missing value
FAT: bogus sectors per cluster 0
VFS: Can't find a valid FAT filesystem on dev sdb1.

[B]I found GNU ddrescue and downloaded via Synatptic.
Can someone please guide me step by step in using gddrescue?[/B]


Thank you,

Doug

---

