---
title: "Numbering of the ATA devices?"
date: 2008-10-19
forum: Hardware
---

### Post by Schuttwegraeumer on 2008-10-19
I need the numbering schemata of the ATA devices.
I have a problem with ATA1.00.
I have a PATA System with 2 connectors.
On the first connector are 2 HDs and on the second connector is only one DVD.
Is ATA1 the complete connector or the first/second device?
How can I list all these devices?

---

### Post by IcarusR on 2008-10-20
First ATA drive will be hda first partition on that drive will be hda1 & second hda2.
Second ATA drive will be hdb first partition on that drive will be hdb1 & second hdb2.

To see a list of all attached drives ```
sudo fdisk -l
```
password will be your normal user password.
On my system this gives....

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc423cc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2590    20804143+   7  HPFS/NTFS
/dev/sda2            9459        9729     2176807+  82  Linux swap / Solaris
/dev/sda3            2591        9458    55167210   83  Linux

```

So I have one SATA drive sda with 3 partitions, NTFS, Linux swap & Linux (system)

Hope that helps you.

---

