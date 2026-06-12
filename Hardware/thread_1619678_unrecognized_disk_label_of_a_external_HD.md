---
title: "unrecognized disk label of a external HD"
date: 2010-11-12
forum: Hardware
---

### Post by COKEDUDE on 2010-11-12
I have a external HD that I can't seem to open. When I try to open it with gparted it says unrecognized disk. When I run gparted from the terminal this is what it says. 

```
~ $ sudo gparted
======================
libparted : 2.2
======================
/dev/sdb: unrecognised disk label
```

When I run the fdisk command this is what it says. 

```
~ $ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c8b89

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1245     9999360   83  Linux
/dev/sda2            1246        5478    33998849    5  Extended
/dev/sda3   *        5479       12161    53681197+   7  HPFS/NTFS
/dev/sda5            1246        1743     3998720   82  Linux swap / Solaris
/dev/sda6            1744        5478    29999104   83  Linux

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
```

---

### Post by COKEDUDE on 2010-11-12
I also get this message when I try to mount the HD. I tried with and without the force option. 

```
~ $ sudo mount -t ntfs-3g /dev/sdb /media/hd-ntfs -o force
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

~ $ sudo mount -t ntfs-3g /dev/sdb /media/hd-ntfs
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

---

### Post by COKEDUDE on 2010-11-12
For some reason I can now see my partition in Nautilus (my file manager) but I can't mount it. 

When I do this command should which one should I be using? 
sudo fdisk /dev/sdb
sudo fdisk /dev/sdb1

Also more information is showing up in sudo fdisk -l. The first time I tried it I couldn't see the part I am putting in between stars below. 


~ $ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c8b89

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1245     9999360   83  Linux
/dev/sda2            1246        5478    33998849    5  Extended
/dev/sda3   *        5479       12161    53681197+   7  HPFS/NTFS
/dev/sda5            1246        1743     3998720   82  Linux swap / Solaris
/dev/sda6            1744        5478    29999104   83  Linux

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9503c6ab

**************************************************************************************************************************
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24792   199141708+   7  HPFS/NTFS

**************************************************************************************************************************

It now thinks I at least have a valid partition table.

---

### Post by COKEDUDE on 2010-11-16
Any ideas please?

---

### Post by COKEDUDE on 2010-12-11
Guess no one has ideas :(.

---

