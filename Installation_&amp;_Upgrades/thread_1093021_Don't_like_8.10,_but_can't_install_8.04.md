---
title: "Don't like 8.10, but can't install 8.04"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by kwabena39 on 2009-03-11
Hello,

I have installed ubuntu 8.10, 64-bit  on my machine and I don't like it.  My Vlc doesn't play downloaded youtube files, and my totem doesn't work well, and friends told me that 8.10 changes too much, obliterating things that previously worked upon upgrades.  I just built a new computer using Gigabyte motherboard, Intel Core 2, Quad 8200, with AMD ATI Radeon HD 4670 video card.  My hard drive is SATA

I want to go back to ubuntu 8.04, Hardy Heron.

PROBLEM: My 8.04 CD doesn't detect a disk in G-Parted, nor does it be able to install.

Here's why I think might be the reason why:

Although I changed my bios to boot up CD first, my CD is on an IDE strip, because I brought it in from my old computer, but my hard drive is a new hard drive in SATA.

Basically, my CD drive can't "see" my hard drive, for some reason.  What do I do?  Do I have to mount my hd first?  Where?  Mnt?  Media?  Where can I find my hard drive?

Oh, and another thing, what about if I want to wipe my disk clean?  Is there a good disk wiper that dan wipe new disks that use RAID?  My old disk wiper, DBAN, is not good for either SATA or Raid.

Any help would be greatly appreciated.

Thanks

---

### Post by tommcd on 2009-03-11
Try Ubuntu 8.10 32 bit. You likely will not have those problems with 32 bit Ubuntu, and 8.10 has newer stuff.

If you *really* want 8.04:
What chipset does your motherboard use? Please post it here. If it is a very new chipset, it is possible that the slightly older kernel in 8.04 does not support your chipset.
Does you BIOS have an option for "IDE mode" or something like that in the BIOS? Try different options for the hard drive settings in the BIOS.
Try installing 8.04 by hitting F6 to enter boot options, and type **all_generic_ide** to boot with that option.

I think your best option though, especially with such a new computer, would be Ubuntu 8.10 32 bit.

---

