---
title: "IRQ Conflict - nVidia and AHCI"
date: 2009-01-07
forum: Hardware
---

### Post by xuanyou on 2009-01-07
I refer to the following thread: [http://ubuntuforums.org/showthread.php?t=734106](http://ubuntuforums.org/showthread.php?t=734106)

I'm getting the exact same problem on my computer, although it only seems to be happening with a certain laptop (Asus G2S). In summary, nVidia and AHCI are sharing the same IRQ 16, and they sometimes argue with each other, bringing the whole system down.

The solution posted was to disable ahci, and use the ata_piix module instead, and at the same time switch the BIOS SATA mode from "Enhanced" to "Compatible".

I'm currently on Ubuntu 8.10 with kernel 2.6.27-9, and experiencing the same problems with nvidia-glx-177 and 173.

If I wish to disable ahci, must I recompile my kernel? Anyone on other platforms affected by this issue? If not, I fear that this problem may remain unfixed, as "Linux users on Asus G2S" seems like a small enough group.

TIA.

---

### Post by xuanyou on 2009-01-09
Problem solved.

On the Asus G2S, under the hard drive BIOS,

Block (Multiple Sector) Data Transfer -> Disabled
PIO -> Mode 0
DMA -> Single Word DMA Mode 0
32-bit Data Transfer -> Disabled

Not sure if this is overkill, but it has disabled the ahci driver in Ubuntu, and allowed the nVidia driver free reign over IRQ 16.

---

