---
title: "Hard disks mixed up!"
date: 2007-11-23
forum: Hardware &amp; Laptops
---

### Post by talbain on 2007-11-23
I have 5 hard disks in my pc

ATA 160gb - Dual boot drive (Ubuntu 80gb - XP the rest)
ATA 160gb
SATA 250gb
SATA 163gb
SATA 500gb

sudo fdisk -l shows:

```

homeserver@homeserver:~$ sudo fdisk -l
[sudo] password for homeserver:

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b9b013e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30515   245111706    7  HPFS/NTFS

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10e5e9b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19929   160079661   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9894f92e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2208042

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9546    76678213+  83  Linux
/dev/hda2            9547        9733     1502077+   5  Extended
/dev/hda5            9547        9733     1502046   82  Linux swap / Solaris

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd39be25a

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19929   160079661   83  Linux

```

It seems to be that the 250gb SATA disk is /dev/sda
The problem is that after i added the line:

```

/dev/sda1 /media/sda1  ext3 defaults 0 2

```

into fstab to mount it automatically, /dev/sdb is being mounted! and also i get an error at boot suggesting that i run fsck on that drive or press ctrl+d to continue booting.
Does anyone know what could be wrong?

---

### Post by Linicks on 2007-11-23
According to your fdisk -l output/ sda1 is NOT ext3 filesystem, but NTFS.

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30515   245111706    7  HPFS/NTFS
```

```
/dev/sda1 /media/sda1  ext3 defaults 0 2
```

Nick

---

### Post by talbain on 2007-11-29
Thanks Nick, sorry for the late reply, you were right, i missed that part (I was kind of stupid posting without taking a harder look at it). Sorry+Thank you gain.

---

