---
title: "Install failed on acer 3000"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by blitz_mohit on 2009-08-30
I have a laptop (acer 3000) with the following configuration:
1.8GHz sempron processor
1.2Gb RAM
60 Gb hard disk
sis shared graphics memory
broadcom wireless network card(air force one)

i tried 3 times to install ubuntu 9.04 from the official disc with the following options
lanuage and keyboard--english 
country--India
Time--Asia/Calcutta
partition--hda9 which has 13gb of space
mount point-/ and type--ext4

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1380    11084818+   7  HPFS/NTFS
/dev/hda2            1381        4057    21503002+  1c  Hidden W95 FAT32 (LBA)
/dev/hda3            4058        7207    25302375    5  Extended
/dev/hda5            4058        4069       96358+  83  Linux
/dev/hda6            4070        4981     7325608+  83  Linux
/dev/hda7            4982        5273     2345458+  83  Linux
/dev/hda8            5274        5589     2538238+  82  Linux swap / Solaris
/dev/hda9            5590        7207    12996553+  83  Linux

the installer reaches installation correctly till 80% but after that it says ubiquity failed and tries to send error message but the compilation of that message also does not complete.

I have already a RHEL5 and winxp runnin on the same machine.Have been using ubuntu since 6.04 and never such a problem.
Is this a documented bug cause i couldnt find anythin...
:confused:

---

### Post by mikewhatever on 2009-08-30
Can you explain what the official disk is. Is that the disk with an iso file you downloaded and burnt? Did you md5sum checked the iso?

---

### Post by blitz_mohit on 2009-08-30
ordered from:::
Order a CD from ShipIt

Ubuntu offers the ShipIt service, which will deliver a small set of Ubuntu CDs to you at no cost. Follow the instructions on the ShipIt website to place an order - delivery will typically take 6-10 weeks.

what i got was an official disk..

---

