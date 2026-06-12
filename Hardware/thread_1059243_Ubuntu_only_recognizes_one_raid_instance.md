---
title: "Ubuntu only recognizes one raid instance"
date: 2009-02-03
forum: Hardware
---

### Post by Tindey on 2009-02-03
I have been having trouble getting my ubuntu server addition to see my second raid configuration. i would greatly appreciate any assistance.


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1bdc0374-bbe6-4e74-acb8-94677523fc0b /               ext3    relatime,errors=remou                                                                  nt-ro 0       1
# /dev/sda5
UUID=f1737825-3977-4da1-b47b-c290f382dac8 none            swap    sw              0                                                                         0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

sean@hotshot:/$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000778ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59322   476503933+  83  Linux
/dev/sda2           59323       60801    11880067+   5  Extended
/dev/sda5           59323       60801    11880036   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table


anyone need any additional information?

---

