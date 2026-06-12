---
title: "BIOS Read full 512MB but Ubuntu/Windows/Memtest86 Reads different"
date: 2011-12-26
forum: Hardware
---

### Post by jgray152 on 2011-12-26
Hi all

This is a laptop I am trying to fix. For the longest time I thought there was a bad mem stick. Yesterday I bought new ram for it but it won't come till Friday. 

So this HP laptop has 512MB (2x256) of ram installed. The BIOS will read all 512MB of memory. Windows / Ubuntu and Memtest86 read different

Ubuntu: 368.9Mb
Memtest86: 383Mb
Windows XP: I forget exactly...It was in the 300-400 range.

I tried each mem stick individually and the BIOS reads 256Mb on each in both memory slots available. Memtest86 reads 127MB in both memory slots available.

Ubuntu froze loading probably cause there was not enough ram so I couldn't see what Ubuntu would read with 1 stick. It has a hard time running on this 368.9 that it sees.

Any idea what could cause this?

_**Some info from Memtest86:**_ 

**With 1 256Mb stick installed**
127MB - 160Mhz (DDR 320) / CAS 2.5-3-3-7 / DDR1 (64Bits)

**With 2 256Mb Stick Installed** (512Mb)
383Mb - 133Mhz (DDR 266) / CAS 2.5-3-3-6 / DDR1 (64Bits)

Some Laptop Specs
32 bit System
Memory Handling Capability: 1GB (2x512) DDR333 PC2700


So what could cause this?

---

### Post by bobsageek on 2011-12-26
Old BIOS might be allocating shared video memory.

---

