---
title: "Transcend Solid State Disk not recognized"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by Eve666 on 2007-12-29
I installed Ubuntu 7.10 Gutsy Gibbon on following hardware:

MSI K9N Neo V3 Motherboard
AMD Athlon X2 BE-2400 Processor
DDR2-800 2048MB Corsair RAM
Fatal1ty 256MB XFX GeForce 7600 GT Graphic Card
2 x 250GB Seagate Barracuda Hard Disks
LG GSA-H66N SATA DVD-RW Drive
Transcend SATA 32 GB 2.5" Solid State Disk

The two Seagate hard disks are recognized as /dev/hda and /dev/hdb. The CD-RW is recognized as /dev/scd0.

My Problem is, the Transcend SSD is not recognized by Ubuntu. It doesn't seem to be a problem with the SATA controller, because my CD-RW drive, which is also attached to SATA, is recognized. And if I attach a SATA hard drive instead of the Transcend SSD, it does get recognized as /dev/sda. The Transcend SSD does not get recognized, it is as if it wasn't there. But the SSD is ok, it is recognized by the Windows XP installation CD and also by FreeBSD 6.2. It is also recognized by OpenSuSE 10.3, but then everything gets really slow, because OpenSuSE seems to turn off DMA for every hard disk.

So what can I do to get Ubuntu to recognize my SSD?

---

