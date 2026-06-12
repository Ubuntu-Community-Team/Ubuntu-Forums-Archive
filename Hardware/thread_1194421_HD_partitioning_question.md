---
title: "HD partitioning question"
date: 2009-06-22
forum: Hardware
---

### Post by hatchet502 on 2009-06-22
I have a dell dimension, 2.4Ghz, 512 mb ram with a 30 gb drive and a 40 gb drive running 9.04.  I manually partitioned the second hd into 2 20gb drives.  One is ext3 and one is vfat.  If I mount both partitons one shows as the whole 40 gb drive and the other 20gb.  If I do a df -h command it shows the same results.  When both are mounted and click on properties same things shows.  If I open gparted it shows it is slplit into 2 20gb drives.  Is something wrong or is this how it shows up?

Thank you

---

### Post by blackxored on 2009-06-22
Couldn't tell for sure. Please paste dmesg about how your hard disk are being detected by the kernel.

---

### Post by hatchet502 on 2009-06-22
[    2.540387] scsi 0:0:1:0: Direct-Access     ATA      ST340014A        8.16 PQ: 0 ANSI: 5
[    2.540545] sd 0:0:1:0: [sdb] 78125000 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.540573] sd 0:0:1:0: [sdb] Write Protect is off
[    2.540577] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    2.540620] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.540731] sd 0:0:1:0: [sdb] 78125000 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.540758] sd 0:0:1:0: [sdb] Write Protect is off
[    2.540762] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    2.540807] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.540813]  sdb: sdb1 sdb2
[    2.559727] sd 0:0:1:0: [sdb] Attached SCSI disk
[    2.559803] sd 0:0:1:0: Attached scsi generic sg1 type 0

this is what I found.

---

