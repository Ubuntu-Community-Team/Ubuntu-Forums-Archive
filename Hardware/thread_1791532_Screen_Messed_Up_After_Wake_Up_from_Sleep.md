---
title: "Screen Messed Up After Wake Up from Sleep"
date: 2011-06-26
forum: Hardware
---

### Post by cg2916 on 2011-06-26
When I open the lid of my laptop, the screen is messed up. It seems to be that this one small square repeats itself throughout the entire screen (will take picture if needed).

Any idea why this happens?

---

### Post by JC Cheloven on 2011-07-07
Some hardware simply isn't compatible with sleeping/hibernation in ubuntu. What pc is it? If you post the output of ```
lspci
``` perhaps will give a clue.

---

### Post by cg2916 on 2011-07-16
> **JC Cheloven said:**
> Some hardware simply isn't compatible with sleeping/hibernation in ubuntu. What pc is it? If you post the output of ```
lspci
``` perhaps will give a clue.

00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

---

