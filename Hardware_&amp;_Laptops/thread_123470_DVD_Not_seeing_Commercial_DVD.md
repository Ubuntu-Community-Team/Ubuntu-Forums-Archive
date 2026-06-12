---
title: "DVD Not seeing Commercial DVD"
date: 2006-01-30
forum: Hardware &amp; Laptops
---

### Post by casperl on 2006-01-30
Hi,

The DVD Writer / Reader is not seeing commercial DVD's.

The DVD is an ASUS DVD writer / reader on the first IDE of a Gigabyte AMD-Athlon system

The content of /etc/fstab is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults           0       0
/dev/mapper/Ubuntu-root /       ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /boot           ext3    defaults           0       2
/dev/mapper/Ubuntu-swap_1 none  swap    sw                 0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto    0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto     0       0
/dev/hde1       /media/smart    auto    noauto,user,exec   0       0

Opening commercial DVD's with Totem reports: 
Failed to find mountpoint for device /dev/hda in /etc/fstab

Opening the same DVD with < mount /cdrom > reports:
mount: block device /dev/hda is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hda,
       missing codepage or other error

dmesg | tail reports:

[4477461.352000] ATAPI device hda:
[4477461.352000]   Error: Not ready -- (Sense key=0x02)
[4477461.352000]   Incompatible medium installed -- (asc=0x30, ascq=0x00)
[4477461.352000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4477461.352000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4477463.401000] ATAPI device hda:
[4477463.401000]   Error: Not ready -- (Sense key=0x02)
[4477463.401000]   Incompatible medium installed -- (asc=0x30, ascq=0x00)
[4477463.401000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4477463.401000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "

mount /media/cdrom0 reports:

mount: block device /dev/hda is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hda,

with dmesg | tail reporting:

[4477488.127000] ATAPI device hda:
[4477488.127000]   Error: Not ready -- (Sense key=0x02)
[4477488.127000]   Incompatible medium installed -- (asc=0x30, ascq=0x00)
[4477488.127000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4477488.127000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "

Using dvd::rip with tcprobe reports:
tcprobe -H 10 -i /dev/hda
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't open file VIDEO_TS.IFO.
(iodump.c) unable to open directory "/dev/hda"

Ditto for tcprobe -H 10 -i /dev/dvd

Happens with 2 different commercial DVD's (all I've tried)
DVD data disks ie. Ubuntu Install DVD is read fine!

Now I've tried pmount, rebooting, this, that, the other.

I'm stumped and I've come to the conclusion that I understand absolutely nothing!

ANY, any help appreciated.

Casper

---

### Post by Nikusan on 2006-01-30
[This entry]("https://wiki.ubuntu.com/RestrictedFormats#head-cd84b8e23927ccdb4bb55ffd3074687abec0cf3b") in the wiki might help you.

---

