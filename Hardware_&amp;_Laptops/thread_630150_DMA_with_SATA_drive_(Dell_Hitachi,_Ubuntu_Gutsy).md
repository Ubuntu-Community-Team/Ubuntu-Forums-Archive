---
title: "DMA with SATA drive (Dell Hitachi, Ubuntu Gutsy)"
date: 2007-12-03
forum: Hardware &amp; Laptops
---

### Post by analyzer123 on 2007-12-03
Hello all,
     I installed (clean) Gutsy on my dell E1405 which has a hitachi SATA drive. I was reading the forum and came across a thread which said DMA does not work with SATA drives in linux. I checked with hdparm -d1 /dev/sda3 and it fails with the error:
 HDIO_SET_DMA failed: Inappropriate ioctl for device

The SATA drives does have DMA capabilities. If I do a hdparm -i, it gives:
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
Drive conforms to: ATA/ATAPI-7 T13 1532D revision 1:  ATA/ATAPI-2,3,4,5,6,7

Is the drive being correctly recognised as SATA not and ATA? Dpes DMA work in linux with SATA? How do i make is work?

Thanks.

---

### Post by tighem on 2007-12-10
Lots of folks are reporting this problem and there is a bug report opened:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96693](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96693)

It says "Fix committed" but no one has seen a fix yet...

---

