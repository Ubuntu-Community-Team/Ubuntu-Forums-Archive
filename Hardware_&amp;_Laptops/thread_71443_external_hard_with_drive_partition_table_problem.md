---
title: "external hard with drive partition table problem"
date: 2005-10-03
forum: Hardware &amp; Laptops
---

### Post by Liroth on 2005-10-03
Hi, for two days now my ubuntu doesn't like my external 160GB FAT32 hard drive anymore. in former times it was just detected and mounted automatically. now ubuntu tells me Disk /dev/sda doesn't contain a valid partition table. anyway i can still access it when using windows XP. i've had the problem some time ago but it was fixed when i reinstalled ubuntu. but as this can't be called a solution, i would like to know how to make ubuntu mount my hard drive again.

---

### Post by Liroth on 2005-10-05
Maybe it can help:
fdisk told me
Code:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition tablet

fstab says:
Code:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

