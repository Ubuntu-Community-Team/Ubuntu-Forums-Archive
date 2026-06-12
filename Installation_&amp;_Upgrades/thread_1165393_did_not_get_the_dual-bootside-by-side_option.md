---
title: "did not get the dual-boot/side-by-side option"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by mikulator on 2009-05-20
Well I have been running Ubuntu on my laptop for some time now and with great succes and thus it was time to put on my home-office desktop.

It has 2 XP partions and I freed up some space for Ubuntu / about 60 GB.

Booted on CD (version 9.04) and expected - as I has read an seen on several guides - that I would be able to decide where to install Ubuntu (Free Space). From the "Prepare disk space" screen Ubuntu did state that it had found the 2 XP partions and the free space, but it only gave me the option to use the entire disk.

What went wrong? 

Cheers
Mik

Just to add:
Does it have anything to do with the number of primay partitions which Ubuntu sees?
My disk is currently configured:
1) XOSL                     Primary
2) recovery (for XP 2) Primary
3) work XP                 Primary
4) home XP                Primary
5) Unallocated            Logical

---

### Post by Mark Phelps on 2009-05-20
> **mikulator said:**
> 
Does it have anything to do with the number of primay partitions which Ubuntu sees?

Quite possibly.  You can't have more than four primary partitions on a single drive, but it's possible to install Ubuntu entirely in an Extended partition. Also, you said to use the entire disk, which if it worked, would have wiped out ALL your partitions and repartitioned the drive.

---

### Post by mikulator on 2009-05-21
I didn't go for the full installation, but found a old 80 GB disk and used that.

Thanks, I will try the extended partition idea.

---

