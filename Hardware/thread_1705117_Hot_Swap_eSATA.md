---
title: "Hot Swap eSATA"
date: 2011-03-11
forum: Hardware
---

### Post by tail.kinker on 2011-03-11
I have an eSATA bay that I wish to use hot-swappable.  Unfortunately, it doesn't want to work.  I've tried using scsiadd, as well as directly pushing a scan request through /sys/class/scsi_host.

Here is the relevant hardware information:

*20:00.0 RAID bus controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
*ThermalTake BlacXDuet (which works fine under USB)
*Western Digital WD2500AAJS SATA HDD
*Western Digital WD5000AAKS SATA HDD
*Seagate Barracuda ST31608

The device detects fine on bootup, but not when powering up from cold.

---

### Post by vcrpcant on 2012-05-12
I'm also interested on this :)

---

### Post by elvenb on 2012-05-12
Check your BIOS settings.  You should be using AHCI rather the SATA controller, and then make sure you have hot-swappable enabled for that particular port.  (This applies, at least, to a SuperMicro Server running Linux.)  

Here's a link that apparently applies to Windows [http://forums.pcper.com/showthread.php?t=444831](http://forums.pcper.com/showthread.php?t=444831)

---

