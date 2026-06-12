---
title: "Wireless Card Stopped Working under 2.6-24-24-386"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by davidr00 on 2009-07-25
My Ubuntu 8.04 install has worked with the wireless card on my laptop since I installed Ubuntu. My laptop is an Dell Inspiron 1420 that came with Vista installed. I am dual booting it with Vista and Ubuntu. 

When I boot under 2.6.24-24-386 I can't seem to access my wireless card. However, if I boot under 2.6.24-24-generic, my wireless card works without problem like it use to. This problem just started sometime this week. Before that I hadn't logged on in a couple of weeks.

Any assistance would be appreciated.
Thanks,
~David

Here is the output of lspci:

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

### Post by davidr00 on 2009-07-25
I guess I'll try openSuse.

---

### Post by digital-radio on 2009-07-30
I am a Linux user, not a Linux programmer so when I upgraded from 8.04 to 9.04 my D-Link wireless card failed to work.   Network manager gives some error code when run it  and I have tried surfing the net to see if there is some fix.   So far nothing has worked and maybe I have messed up the system.   Everything else works including the ethernet connection to the DSL modem.   Ubuntu 8.04 worked great, but it seems Ubuntu 9.04 is a giant step backward.   I upgraded because an upgraded Linux radio application would not work in 8.04 and now does in 9.04.   I need that wireless card working so I don't have to use a 50 foot ethernet cable that someone can trip over.

---

