---
title: "LSI MegaRAID i4 poor write performance"
date: 2007-11-25
forum: Hardware &amp; Laptops
---

### Post by Roland of Gilead on 2007-11-25
For the last several months, I'd been running a fileserver in my office using Ubuntu Feisty without any issues.

The box is an old Dell Dimension XPS T800 (Pentium 3 @ 800MHz)  w/786MB RAM.  It's got an LSI MegaRAID i4 PATA host adapter installed, with four 250GB PATA drives configured into a single RAID 5 logical drive (sda).  Each drive is connected to a separate channel on the card by an 80-wire ATA cable.

Being my first time out, I dropped in the Feisty CD, booted and installed everything onto sda, using 2GB for swap space and the other 748GB for the root filesystem.  I didn't bother with benchmarks or any such, but the few times I used FTP to move large files onto it, I recall the limitation on speed being the 100MBit lan, permitting about 11MB/sec writes.

So, today was upgrade day, as my array had run out of space.  The 250GB drives have been replaced by 500GB drives, and I configured it thusly:

Logical Drive 1 = sda
12GB RAID 0, 64KB stripe

Logical Drive 2= sdb
1.5TB RAID 5, 128K stripe


My intent was to install Gutsy using the RAID 0 drive for swap space and the root filesystem to get better OS performance...and then mount the RAID 5 drive and use it for media files only.

The OS install went fine, but when I started moving data onto the big logical drive, it was crawling.  So, I started doing benchmarks with dd and FTP.

As expected, I get great performance from my RAID 0 volume...writes on the order of 12-30MB/second sustained.

The RAID 5 volume, on the other hand, gets about 4-6MB/sec sustained.

Anyone have any pointers on this kind of setup?

---

