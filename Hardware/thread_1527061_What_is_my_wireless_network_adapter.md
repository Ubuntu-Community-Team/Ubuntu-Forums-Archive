---
title: "What is my wireless network adapter?"
date: 2010-07-08
forum: Hardware
---

### Post by bradley002 on 2010-07-08
I need a driver so that Windows recognizes my wireless network adapter. I did lspci but I don't even know which one of these is my wireless adapter. I definitely have one, I am connected with it right now. Can you help me? 

What driver do I need?

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:03.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

---

### Post by S.R on 2010-07-08
02:03.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev  01)

---

### Post by bradley002 on 2010-07-09
Yep, it worked, thanks.

---

