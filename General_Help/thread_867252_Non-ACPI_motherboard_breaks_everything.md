---
title: "Non-ACPI motherboard breaks everything"
date: 2008-07-22
forum: General Help
---

### Post by RandomMatt on 2008-07-22
(I know this is probably in the wrong forum, but I didn't know whether it was supposed to be in hardware, server platforms, general or Ubuntu)

I ran Ubuntu Server on a L440GX+-based tower (can't really call it a server, it's just really a desktop with a 2xSlot1 SMP motherboard) until said L440GX+ motherboard failed. I just today replaced it with a [Tyan Thunder 2500]("http://www.tyan.com/archive/products/html/thunder2500.html"), which has **no ACPI**, and all hell broke loose.

I know it isn't a problem with Ubuntu or anything, but the first thing I noticed is that, on the two 1GHz/256 cache/133MHz FSB Pentium 3 slot-1 processors I swapped in, the BIOS fails to "update microcode" on them. I'm guessing this is because the BIOS doesn't properly support 1GHz processors, because it detected them as 733MHz and the 550MHz pair that came with it did not do this.

When I went into GRUB, it went onto a blank screen with a blinking cursor in the top-left, then, a while later, printed "GRUB" at the top-left and sat idle.

I tried to fix the installation using a Ubuntu 7.10 (I think) LiveCD, but, even with "acpi=off", it spat out an APIC timing or something error and died at the splash.

I have a feeling that this motherboard is too old and weird for modern Linux... Is there anything I can do?

---

