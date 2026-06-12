---
title: "ntfs mount??????? cfdisk error - need help"
date: 2005-11-30
forum: Hardware &amp; Laptops
---

### Post by mboto on 2005-11-30
hi there,
i got big problems mounting a win ntfs partition.

when i type sudo cfdisk - always the message:

"FATAL ERROR: Cannot open disk drive, Press any key to exit cfdisk"

with gparted i can see the hard disk (120gb) as hdd.

i mounted this disk half a year ago without problems...

what could cuas my troubles??

don`t know what to do..

my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc3       /home           ext3    defaults        0       2
/dev/hdc1       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


if i write:

sudo fdisk -l

comes:

Platte /dev/hdc: 61.4 GByte, 61492838400 Byte
255 K&#246;pfe, 63 Sektoren/Spuren, 7476 Zylinder
Einheiten = Zylinder von 16065 &#215; 512 = 8225280 Bytes

   Ger&#228;t  boot.     Anfang        Ende     Bl&#246;cke   Id  System
/dev/hdc1               1         243     1951866   82  Linux Swap / Solaris
/dev/hdc2             244        2735    20016990   83  Linux
/dev/hdc3            2736        7476    38082082+  83  Linux

Platte /dev/hdd: 123.5 GByte, 123522416640 Byte
255 K&#246;pfe, 63 Sektoren/Spuren, 15017 Zylinder
Einheiten = Zylinder von 16065 &#215; 512 = 8225280 Bytes

   Ger&#228;t  boot.     Anfang        Ende     Bl&#246;cke   Id  System
/dev/hdd1               1       15017   120624021   42  SFS

but wenn i try to mount hdd1 with:
sudo mount /dev/hdd1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

comes:
mount: Ger&#228;tedatei /dev/hdd1 existiert nicht (devicefile /dev/hdd1 does not exist)


dont know any further

please help

---

### Post by aysiu on 2005-11-30
Is SFS German for NTFS?

---

### Post by mboto on 2005-12-01
no it is not - it is just like in english - ntfs and fat(32).

don`t know what sfs is - but the second hard disk is formatted with ntfs - of that i`m sure

---

