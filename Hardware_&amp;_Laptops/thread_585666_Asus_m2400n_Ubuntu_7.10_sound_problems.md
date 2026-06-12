---
title: "Asus m2400n Ubuntu 7.10 sound problems"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by stric1 on 2007-10-21
Hi to all!

I'm an absolute beginner in linux. I installed Ubuntu 7.06 (now uograded to 7.10) and sound is notworking at all. My lspci:

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
01:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
01:03.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
01:03.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
01:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:05.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

Anyone has an idea what should I try?

By the way, with Ubuntu 6.10 sound worked ok. 

I would be very happy if anyone can help me!

---

### Post by Jshippee on 2008-01-10
I also have an Asus M2400n with Ubuntu 7.10 with no sound.  I have tried everything I could find on every forum I could find and nothing seems to make any difference.  Is there really nothing that can be done with this motherboard and sound card combo?

---

### Post by Yellow Pasque on 2008-01-10
Try this yet?
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by edeatie on 2008-01-10
I have the same computer. Just re-install gutsy with nolapic. After that, sounds are working.

---

### Post by Jshippee on 2008-01-15
Wow, I worked for hours trying to fix this!  I appreciate the easy fix, everything works great now!

---

### Post by mobileking on 2008-01-15
thats good !  :)

---

