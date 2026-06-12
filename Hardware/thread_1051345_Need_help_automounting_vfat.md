---
title: "Need help automounting vfat"
date: 2009-01-26
forum: Hardware
---

### Post by yusuo85 on 2009-01-26
Im trying to load two vfat drives at boot, now they do this successfully problem being I am unable to make and changes, I dont have write access.
Can someone look over my fstab and see whats wrong, the current config has never been a problem before
Heres the fstab

--------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda5
UUID=1019bd49-0819-4de5-af23-6beb505e50e1 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda3
UUID=1105ec11-e1de-4888-8184-51c5a1b03fb0 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda4 /media/media vfat defaults 0 0
/dev/sdb1 /media/media2 vfat defaults 0 0
--------------------------------

heres fdisk info
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x544c552e

Device Boot Start End Blocks Id System
/dev/sda1 * 1 3149 25294311 7 HPFS/NTFS
/dev/sda2 3150 6152 24121597+ 5 Extended
/dev/sda3 6153 6213 489982+ 82 Linux swap / Solaris
/dev/sda4 6214 30401 194290110 b W95 FAT32
/dev/sda5 3150 6152 24121566 83 Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb753b753

Device Boot Start End Blocks Id System
/dev/sdb1 1 30401 244196001 b W95 FAT32

---

### Post by yusuo85 on 2009-01-26
/dev/sda4 /media/media vfat	auto,user,exec,rw,async 0 0
/dev/sdb1 /media/media2 vfat	auto,user,exec,rw,async 0 0

---

