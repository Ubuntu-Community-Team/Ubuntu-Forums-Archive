---
title: "wireless adapter issue"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by pbhound on 2009-03-27
im trying to install a linksys pcmcia card using the windows driver. but i dont have the option to use the windows driver.inf.

here is the code from lpci

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory 
Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
02:03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
02:06.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
02:06.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
02:0f.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)


thanks for the help

---

### Post by Mark Phelps on 2009-03-29
You have a Broadcom 4306 chipset -- you will need to use NDISWrapper to get wireless working.

That's far too complicated to go into here.

Go the the networking subforum and search on NDISWrapper.  You'll find posts dealing with exactly that chipset and how to install NDISWrapper and get it working.

---

