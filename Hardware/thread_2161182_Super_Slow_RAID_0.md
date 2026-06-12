---
title: "Super Slow RAID 0"
date: 2013-07-09
forum: Hardware
---

### Post by Quantumkiwi on 2013-07-09
Hi all,
I'm putting together a large file server for medium-term backups of scientific data. 

Here's the specs:
24x WD30EZRX 3TB 64MB Cache Hard Drives (145MB/s sustained as stated by WD's website)
LSI 3ware 9750-24i4e raid controller
2x AMD Opteron 246 2GHz CPUs
3Gb DDR ram
ST3750640AS 750Gb boot drive
(Not sure what mobo)
850W PSU
Radeon 7000 64mb DDR Graphics Card
and  Ubuntu 12.04.2 32-bit

RAID specs:
Stripe: 256k
Write Cache: Enabled
Read Cache: Intelligent
StorSave Profile: Performance
Auto-Verify: Enabled

Currently,  I am getting best case speeds of ~300Mb/s with Mb and larger files.  This kind of speed is all nice and great, but I really need above a Gb/s  as I will be moving Tb's of data around.

I have set a larger  stripe (using:  blockdev --setra) as I am working with rather large  files, but this results is only around a 10% increase.

DISCLAIMER: I am not, by any means, a Linux expert. If you have some tips that would help me here, please post! Thanks!

---

### Post by papibe on 2013-07-09
duplicated thread here: [http://ubuntuforums.org/showthread.php?t=2161181](http://ubuntuforums.org/showthread.php?t=2161181)

Please do not create 2 or more threads with the same content. It is very difficult to offer help when the conversation is divided into several threads. Please continue on the other thread.

**Thread closed**.

---

