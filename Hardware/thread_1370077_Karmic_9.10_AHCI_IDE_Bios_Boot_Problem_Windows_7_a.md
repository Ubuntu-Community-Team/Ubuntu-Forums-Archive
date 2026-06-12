---
title: "Karmic 9.10 AHCI /IDE Bios Boot Problem Windows 7 and USB Devices"
date: 2010-01-01
forum: Hardware
---

### Post by ChrisMoore0908 on 2010-01-01
**Summary**. Attaching multiple USB devices (mouse, 3G modem and memory stick/pen drive) “solves” Karmic’s AHCI booting problem. Clearly, there is something significantly wrong with the kernel AHCI support in Ubuntu 9.10
**Hardware**
Brand new Packard Bell (eg Gateway) DotMU netbook; 11.6” screen
Intel Celeron 743 single core 64 bit processor
250GB HDD
OS
Windows 7 64 bit /Karmic Koala 32bit or 64 bit.

I installed Karmic 9.10 in a dual boot setup. Karmic runs well on a live CD. After installing to the HDD and rebooting, Grub 2.0 would run ok, but Karmic would eventually fail to boot showing a Kernel Panic failure. Googling indicated that this could be due to AHCI driver problems in Karmic. Sure enough, if I switch the HDD to IDE management in the BIOS then Karmic boots fine. However, Windows 7 gives BSoD in IDE mode. (This is also a well understood Vista/XP problem, ie Vista supports AHCI and XP doesn’t).
I read another forum post that suggested something very surprising and indicative that this is a significant failure within the Karmic AHCI driver. The other writer noted that his Karmic would boot fine so long as he “had a few USB devices plugged in”. I couldn’t seriously believe that this would have any influence, but I can report here that I confirm this behaviour. If I boot into Karmic without any external USB devises plugged in then the boot fails with a kernel panic. If I plug in eg mouse, pen drives etc then Karmic boots fine when AHCI is “on” in the bios.
This is a very significant issue to users. AHCI support is supposedly kernel bound since 2.6.19 (and I am now at 2.6.31.17) and therefore I don’t expect or accept these problems.

---

