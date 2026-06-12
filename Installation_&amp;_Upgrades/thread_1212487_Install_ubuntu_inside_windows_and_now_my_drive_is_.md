---
title: "Install ubuntu inside windows and now my drive is missing"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by origin248 on 2009-07-13
Hi

Please can anyone figure out what is wrong or how to fix this problem:

I was trying to do a fresh install of Ubuntu 9.04 inside Windows 7 (big mistake I realised that now) and before the installation finish Wubi crashed and I was unable to continue the installation

Now, the entire disk drive is missing from windows.  It still appears under my hardware profile and I tried uninstalling but it still doesn't appear again in Windows.

Big advanced thanks to anyone who can help

---

### Post by starcraft.man on 2009-07-13
Lucky I happened here, I've helped recover a few disks in my time. Ok few questions up front. Please answer the following:

This internal or external hard drive?
What connector - IDE, SATA?
When you say drive, do you mean a whole HDD or simply a partition on it?
When you say fails to appear, you mean in My computer, yes? 
The crash, did you crash the whole computer (i.e. manual reset, bsod...) or just Wubi installer (i.e. program lock up, then terminated task manager, continued working)?
Most important, are there critical files that need recovering? Or is this drive's data expendable and backed up?

My first inclination, assuming it's just the partition on the drive not showing is some sort of serious write error, maybe messed with partition table. Can be fixed, please answer questions though before I give steps.

---

### Post by origin248 on 2009-07-14
Ah, thanks for the reply, finally fixed it with a better disk management software.


For the benefit of anyone who might have the same problem: Basically only wubi crashed during installation and somehow scrambled the partition tables and so no software was picking up the drives and it's partitions.  Basically all I needed to do was change the file system from "h42" back to NTFS again and the drive and all it's partitions are working again.

---

### Post by starcraft.man on 2009-07-14
Glad you got it fixed, that was my hunch. We have a good util for fixing such messes and reconstructing partition tables. [TestDisk]("http://en.wikipedia.org/wiki/TestDisk").

A note for anyone else coming across this.

---

