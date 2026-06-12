---
title: "Not loading driver for IDE device. Can it be forced?"
date: 2009-09-17
forum: Hardware
---

### Post by BrianHere on 2009-09-17
I'm working with Intel AMT and ubuntu 9.04.  As a part of AMT, the motherboard provides an "IDER" device that is a IDE floppy and cd-rom.  I need to be able to access these devices.

When I run "lspci -v", I see that the kernel is recognizing that the device is there.  It shows up as an IDE interface.  However, I can also see in lspci that no kernel driver is in use for the device.  Is there any way that I can force some sort of generic ide driver to try to use the device?

I've tried doing "modprobe ide_generic", however I get "FATAL: Module ide_generic not found."  So, I'm thinking that the ide_generic module is no longer part of ubuntu.

Thanks in advance!

---

### Post by jdsanchez473 on 2009-09-22
I'm having the same problem with my Netfinity 5000 server.. i get an error stating the cd-rom drive cannot be found. In 8.04 i was able to modprobe ide_generic and it would pick it right up after that, but evidently in 9.04 this module has been removed or renamed, someone please help!! or give a clue of other modlues that may work.

---

