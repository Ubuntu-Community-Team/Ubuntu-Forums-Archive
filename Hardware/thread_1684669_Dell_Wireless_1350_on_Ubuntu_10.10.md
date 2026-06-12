---
title: "Dell Wireless 1350 on Ubuntu 10.10"
date: 2011-02-09
forum: Hardware
---

### Post by SNYP40A1 on 2011-02-09
I have an older laptop that I installed Ubuntu on last night.  Ubuntu is working fine for everything except the PCI wireless card.  Is anyone using their Dell 1350 wireless card on Ubuntu 10.10?  If so, how was it setup?  I have seem similar threads for older versions of Ubuntu that involves creating a wrapper around the windows driver which seems overly-complicated.  I'm hoping that the installation has been streamlined since then.

---

### Post by gordintoronto on 2011-02-09
Ndiswrapper seems to be the solution. There are tutorials on Youtube.

Here's the "faint hope clause." Your wireless card says Dell 1350 on the outside, but what is on the inside? Open Accessories/Terminal and enter the command:
lspci
One of the lines will include "802." and that's the wireless card. Mine says:
03:07.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

If I had your problem, I would Google ar2413 linux and see what came up.

Second faint hope: connect to your router by wire, and run Administration/Additional Drivers

---

### Post by SNYP40A1 on 2011-02-10
> **gordintoronto said:**
> Ndiswrapper seems to be the solution. There are tutorials on Youtube.

Here's the "faint hope clause." Your wireless card says Dell 1350 on the outside, but what is on the inside? Open Accessories/Terminal and enter the command:
lspci
One of the lines will include "802." and that's the wireless card. Mine says:
03:07.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

If I had your problem, I would Google ar2413 linux and see what came up.

Second faint hope: connect to your router by wire, and run Administration/Additional Drivers

Actually, it's now much easier than that.  There's an icon which pops up for restricted drivers.  It auto installs once I connected it to wired connection to take the update.

---

### Post by staufinc on 2011-02-18
I have a Dell latitude D600 with supposedly the same wireless card, but I cannot figure out how to get the drivers. Here is the lspci info:

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

---

