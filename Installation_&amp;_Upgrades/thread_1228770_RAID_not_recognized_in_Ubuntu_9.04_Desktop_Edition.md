---
title: "RAID not recognized in Ubuntu 9.04 Desktop Edition"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by NiKoLai_ on 2009-08-01
Hi, I don't know if this message should be here, please move it if it is not into an appropiate place.


I have 4 HD in my PC. Three with 500 GB and 1 with 1 TB. Two of the 500 GB ones are configured as an RAID 1 (mirroring) array. As the mainboard BIOS forces me to do so, the others are configured as JBOD (two discs, two independent arrays). The mainboard is a Gigabyte M56S-S3. All the discs are Seagate.


I installed Windows XP SP3 with no problem. Windows recognized the mirroring array as a one drive, and the two disks in JBOD as two independent drives. Then, I installed Ubuntu 9.04 Desktop Edition in the same disc I installed WinXP, but in a different partition. Grub was installed in the Linux partition. Both WinXP and Linux boot successfully and with no problem.


The problem is when booting Ubuntu, it doesn't recognize the mirroring as one drive, handling it as two independent drives. After rebooting, BIOS doesn't recognize the arrays (whose were configured using the BIOS as should - in theory - be independent of any OS present on the machine). To solve this, I disconnect one of the JBOD disks and reboot. Then all the connected arrays are recognized. After connecting the disconnected disk again, all the arrays are recognized... Until I boot Linux again.


I would like Ubuntu to recognize the mirroring array as one drive and not make all the drive arrays disappear on reboot. The Ubuntu install was made using the default installed and not including extra command or drivers. Any idea about the problem could be?


Thanks in advance.

---

