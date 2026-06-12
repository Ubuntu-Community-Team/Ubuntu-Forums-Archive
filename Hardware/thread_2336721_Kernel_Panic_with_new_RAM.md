---
title: "Kernel Panic with new RAM"
date: 2016-09-10
forum: Hardware
---

### Post by autocrat on 2016-09-10
Hello!

Today i received new RAM for my desktop and put it in. Ubuntu 16.04 would not boot. It went into a "kernel Panic" state. 

I swapped out the HDD for a backup that had Ubuntu Mate 16.04 on it, and this booted up just fine, it recognizes the new RAM as well. 

Specs before:
CPU: Intel® Core™2 Duo CPU E8500 @ 3.16GHz × 2 
4 GB: 2GB x2 DDR2 800MHz 
500 GB 7200 RPM Western Digital (Ubuntu)

Specs After: 
CPU: Intel® Core™2 Duo CPU E8500 @ 3.16GHz × 2 
8 GB: 2GB x4 DDR2 800MHz 
500 GB 7200 RPM Seagate (Ubuntu MATE)


I ran Memtest86 for a few passes, no errors. 

I removed and reseated all of the RAM, this did not resolve it.

RAM is all the same, so it is not a compatibility issue with the hardware. 

Any help would be appreciated. I would like to get back to running regular Ubuntu on my better HDD.

---

### Post by pqwoerituytrueiwoq on 2016-09-10
try booting a older kernel from grub on your main drive
also you need to use memtest86+, memtest86 can't test over the 32bit ram limit

Did you mix ram sticks? you may need to set ram timings manually in your bios

---

### Post by autocrat on 2016-09-12
> **pqwoerituytrueiwoq said:**
> try booting a older kernel from grub on your main drive
also you need to use memtest86+, memtest86 can't test over the 32bit ram limit

Did you mix ram sticks? you may need to set ram timings manually in your bios

BIOS looks good.
Tried 86+, ran it for a few hours.

Debian, Zorin, Ubuntu Mate, & Steam OS all work fine. Vanilla is the only one having the issue.

---

