---
title: "Automatic mounting fails"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by heruan on 2007-10-19
I have just installed a fresh Ubuntu Gutsy System.
When I connect an external USB hard disk, Gnome tries to automount it but gives me:
```

Cannot mount volume. Invalid mount option when attempting to mount the volume.

```
I tried with more than one disk, all FAT32. Always the same error!

A simple "mount /dev/sdb1 /media/disk" works perfectly!

This is my disk's partitions table:
```

# fdisk /dev/sdb

The number of cylinders for this disk is set to 14593.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x123e1723

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    b  W95 FAT32

```

---

