---
title: "Partition file (/dev/sda1) is not created"
date: 2008-09-10
forum: Hardware
---

### Post by Rawbin on 2008-09-10
Hi there,

I'm having a problem mounting a harddisk connected via an IDE (PATA) cable.

sudo fdisk -l lists the partition as existent: (german ubuntu)
> 
Platte /dev/sda: 120.0 GByte, 120034123776 Byte
255 Köpfe, 63 Sektoren/Spuren, 14593 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xfdaffdaf

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1       14593   117218241    7  HPFS/NTFS

Platte /dev/sdb: 203.9 GByte, 203928109056 Byte
255 Köpfe, 63 Sektoren/Spuren, 24792 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xf443a74d

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1   *           1        2865    23013081    7  HPFS/NTFS
/dev/sdb2            2866       24792   176128627+   f  W95 Erw. (LBA)
/dev/sdb5            2867        5377    20169607+   7  HPFS/NTFS
...


But when trying to mount the partition with
> sudo mount /dev/sda1 -t ntfs /mnt
(with or without force)
this error is printed:
> ntfs-3g: Failed to access volume '/dev/sda1': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.

I've checked the /dev folder, i can find the "sda" file but the partition file "sda1" is missing.

Gparted finds the partition too but prints the warning:
> The device /dev/sda1 doesn't exist

Thanks for your help,
and please excuse any linguistic blunders,

Robin

---

