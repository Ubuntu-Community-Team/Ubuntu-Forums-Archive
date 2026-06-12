---
title: "Disk partitions named 'sda' instead of 'hda'"
date: 2007-04-10
forum: Hardware &amp; Laptops
---

### Post by theonlykman on 2007-04-10
I dont have any problems associated with this and everything is mounted fine, but is there a reason why my disk partitions are named sda instead of hda? Actually, while youre at it could someone explain what the difference is?

> khalid@khalid-laptop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3412    27406858+   7  HPFS/NTFS
/dev/sda2            5962        7238    10257502+  83  Linux
/dev/sda3            7239        7297      473917+   5  Extended
/dev/sda4            3413        5961    20474842+   c  W95 FAT32 (LBA)
/dev/sda5            7239        7297      473886   82  Linux swap / Solaris

Partition table entries are not in disk order
khalid@khalid-laptop:~$ 


---

### Post by moffa on 2007-04-10
For me, my SerialATA hard drive was named sda where as my ide hard drive was named hda.  It probably has to do with the type of hard drive controller.  I think the only difference is cosmetic.

---

### Post by theonlykman on 2007-04-10
Thanks, I guess it is that simple.

---

### Post by Jagot on 2007-04-10
This is as a result of new drivers in the kernel used by Feisty.  Apparently, the new parallell ATA drivers use the same libata infrastructure as the SATA drivers.

---

