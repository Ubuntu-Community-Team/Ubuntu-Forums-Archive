---
title: "Acessing a SD card"
date: 2009-04-13
forum: Hardware
---

### Post by Montalo on 2009-04-13
When i put in my SD card into my internal SD card reader, i can not acess any of the picture and files on it like say, i could do with a cd or a USB memory stick



my question is, what do i need to do (in simple, stupid novice words) to be able to acess and use my SD card?

EDIT: I am using Jaunty, if that helps at all

---

### Post by SuperSonic4 on 2009-04-13
It should get put onto the system under places. You may need to double click on it to mount. If that doesn't work can you give the filesystem (probably vfat) and the place where it is on the pc using ```
sudo fdisk -l
```

---

### Post by SathyaBhat on 2009-04-13
do you get any error messages ? 

Eject the SD card, and insert it back in. If nothing happens, open terminal and type
```
dmesg | tail
```
and paste the contents here.

---

### Post by Montalo on 2009-04-13
> **SuperSonic4 said:**
> It should get put onto the system under places. You may need to double click on it to mount. If that doesn't work can you give the filesystem (probably vfat) and the place where it is on the pc using ```
sudo fdisk -l
```

when i did that, i got back


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5f251d77

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18255   146633256    7  HPFS/NTFS
/dev/sda2           28976       30401    11452416    7  HPFS/NTFS
/dev/sda3           18256       28975    86108400    5  Extended
/dev/sda5           18256       28533    82558003+  83  Linux
/dev/sda6           28534       28975     3550333+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

