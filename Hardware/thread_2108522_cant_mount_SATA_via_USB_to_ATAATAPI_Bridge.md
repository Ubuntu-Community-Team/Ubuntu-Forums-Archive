---
title: "cant mount SATA via USB to ATA/ATAPI Bridge"
date: 2013-01-24
forum: Hardware
---

### Post by peacebliz on 2013-01-24
Trying to mount an internal hardrive via a JMicron USB to ATA/ATAPI Bridge. Running 12.10, The drive is NTFS format.

When i plug it in, ubuntu makes that clicking noise that it sees it, but blkid command doesnt show the drive at all. The only tool i found that would detect it is the disks tool. It says its a "JMicron USB to ATA/ATAPI Bridge (0100) Hardrive" then only lists the serial number and sdb1, nothing else.

searched around the net for hours couldnt find anyone talking about this problem, plz help.

---

### Post by peacebliz on 2013-01-26
searching around working on this prob i found this in wikipedia:

JMicron SATA/IDE controllers are often incompatible with some boot loaders. In particular, those using GRUB, such as Ubuntu, cannot boot in some conditions (2006/08, 2.6.17).[13] The 2.6.18 Linux kernel and JMicron controller BIOS 1.06.53[14] solved these incompatibilities, but may not be present in existing products, or may require re-flashing the motherboard BIOS. Other bootloaders such as the Windows NTLDR boot loader and EXTLINUX work fine. It has been fixed by the latest distros.
[https://en.wikipedia.org/wiki/JMicron#Linux_Compatibility](https://en.wikipedia.org/wiki/JMicron#Linux_Compatibility)

make any sense to anyone?

---

