---
title: "how to install dvb-s card in ubuntu"
date: 2008-12-31
forum: Hardware
---

### Post by mgnice on 2008-12-31
I have just installed my kubuntu 8.a in my pc.
I have DVB-S card skystar 2.6 in my pc attached to PCI slot.
In my previous installation, this device was installed by default and I could see it in ifconfig list too.

**BUT now I can not see it when I type ifconfig in command line.**
lspci for my pc is as below:


00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
**00:0a.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02)**
00:0b.0 Communication controller: Analog Devices SM56 PCI modem
00:0d.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 315PRO PCI/AGP VGA Display Adapter


Please Help me what to do to solve this problem.

---

