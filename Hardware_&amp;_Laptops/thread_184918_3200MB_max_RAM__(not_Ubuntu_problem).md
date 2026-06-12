---
title: "3200MB max RAM ? (not Ubuntu problem)"
date: 2006-05-30
forum: Hardware &amp; Laptops
---

### Post by fnord_uk on 2006-05-30
Hi all,

Sorry for being off-topic, but have a general issue with my PC correctly detecting the amount of memory fitted.  I have Dapper Beta installed, and all is good. I decided to increase from 1GB to 4GB, so I could run WinXP in VMWare server.

When I added the extra RAM (all 4 are identical 533MHz DDR2 DIMMS), the BIOS reported 3200MB installed . That's quite a strange total! The mem test offered by Grub reports the same.

The motherboard is an EVS PF5 Extreme, with a Pentium D 805 dual-core CPU installed, running Dapper for AMD64.  It uses a dual-channel memory architecture.  The manual says it supports up to 4GB RAM.

So, if I just fit any two DIMMS in either slot pair, it reads 2048 MB installed, but all 4 gives just 3200.  I haven't yet tried one stick at a time.  With all 4 in, the Grub ram test ran for 3 hours without error.

I accepted excuses years ago about missing 384kB of RAM, but 896MB is too much... 

Any ideas why the ram is apparently missing?

---

