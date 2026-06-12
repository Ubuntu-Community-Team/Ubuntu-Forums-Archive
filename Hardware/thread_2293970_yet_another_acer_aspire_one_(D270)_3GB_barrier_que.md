---
title: "yet another acer aspire one (D270) 3GB barrier question...."
date: 2015-09-08
forum: Hardware
---

### Post by mike353 on 2015-09-08
I have acer aspire one D270-1410 n2600 dual core processor and I have installed 64-bit Lubuntu. I had a 4GB SODIMM in an old laptop, so I decided to try it in the aspire one.

The funny thing is, the BIOS indicates 4096MB RAM, memtest86 agrees, but Lubuntu only sees 3GB?!

free, top, etc say I only have 3GB.

I am running kernel 3.19.0.26 x86_64.

I have read elsewhere that lots of netbooks have crap chipsets and do not support more than 3GB. But I do not think this is the problem: why would the BIOS screen and memtest86 see the full 4GB?

---

### Post by MartyBuntu on 2015-09-08
RAM dedicated to graphics...

---

### Post by mike353 on 2015-09-08
There is on option to use RAM as VRAM in the BIOS. I have the latest BIOS and it has very few options.

At first I had a 2GB SODIMM. Most of it appeared as RAM: 1.8GB, I think.

With the 4GB, specifying mem=4096M in grub kernel boot parameters makes no difference. 

I don't really understand much about the GMA3600 except that it's old and not very well supported in linux.
Nevertheless, I think it has 8MB of VRAM. But lspci only reports 1MB....

UPDATE:
I managed to find an uncrippled ("Unlocked") version of the 1.10 BIOS and flashed it using recovery mode. While there were many more settings, there was no "memory remap" anywhere and the maximum video ram you could allocate was 64MB. 

I also booted a free FreeBSD 10.2 live image (on USB) and it only found 3GB. 

I give up.

---

