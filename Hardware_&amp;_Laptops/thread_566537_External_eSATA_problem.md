---
title: "External eSATA problem"
date: 2007-10-03
forum: Hardware &amp; Laptops
---

### Post by sokairyk on 2007-10-03
I have an Abit IC7-G m/b ( socket 478 ) and has SATA controllers, not SATA II. I bought an external Seagate SATA II drive that came with a PCI SATA II controller and the drive seems to work fine...

Under Windows XP I installed just the drivers for the PCI card an the drive was recognized. Its speed is almost as my internal SATA drives and the system recognizes it every time I turn it on.

Under Ubuntu Linux (7.04) the drive is recognized IF it's turned on at system boot. It has slower speed than in Windows and when unmounted and turned off the sdc1 file (which is the drive) disappears from /dev/ and cannot be remounted until the next restart.

I have searched and got confused 8)

I read that the detection of the drive called hotplug (I think) needs the feature AHCI enabled. Now what I didn't understand is which chipset must support AHCI the southbridge or the SATA controller? And is NCQ enabled through the AHCI or by default or I got it wrong? :confused:

Anyway my main problem is that I cannot mount the drive if its off. I don't know if it's relevant but the filesystem is NTFS and I use ntfsfuse to write.

---

