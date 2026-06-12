---
title: "SATA problem /w SCSI"
date: 2005-09-21
forum: Hardware &amp; Laptops
---

### Post by uservhy56 on 2005-09-21
Ive a Dell Poweredge 800 with which I installed Ubuntu to the main disk that came with it, a 74gb SCSI. Its set-up for file serving etc. and all was working fine. This week I got 2 new 250gb SATA drives and installed them. I went into BIOS and enabled the new drives. Simple. Then saved changes and exited. Then everything was working fine at the startup until... and heres the log...

Uncompressing Linux... Ok, booting the kernel.
etc. etc.

Then Starting Ubuntu
ata1: disabling port
sdb: asking for cache data failed
sdb: assuming drive cache: write through
sdb: asking for cache data failed
sdb: assuming drive cache: write through
pivot_root: No such file or directory
/sbin/init: 428: cannot open dev/console: No such file
Kernel panic - not syncing: Attempted to kill init!


This is the error is from when i removed the first SATA drive from port0 to port 1 while having the 2nd drive in port2. The problem was more or less the same with the other port config.  If I disable the SATA drives from BIOS it will boot into Ubuntu again, no problem. What could be wrong?

---

