---
title: "Laptop D600 Issues"
date: 2008-03-21
forum: Hardware &amp; Laptops
---

### Post by Tomtheman70 on 2008-03-21
I´ve got a couple issues with my brand new install of Ubuntu on my old D600..

First off, it doesn´t recognize my wireless card as actually being enabled, as in when I check the network preferences it doesn´t show up as eth1. Oddly though when I run lspci I get this:
```
tom@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
**02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)**
tom@ubuntu:~$
```

So what do I need to install and how can I get this wireless card working on here?

Second thing that´s quite annoying is the fact that if I want to get a ¨ or an ´ to show up I have to double tap the key otherwise it wants to make special characters after the keystroke..

Please keep in mind that I haven´t had much experience with linux at all so I don´t know all those fancy commands. :/

I´m running Ubuntu 7.1 with Gutsy.

---

### Post by Tomtheman70 on 2008-03-21
Another thing that just came to my attention is that when I hit backspace while web browsing instead of taking me back it does a page up... I think this might have something to do with my keyboard layout.. but I set it to the regular American standard one. :(

---

### Post by Tomtheman70 on 2008-03-21
Nobody? :(

---

