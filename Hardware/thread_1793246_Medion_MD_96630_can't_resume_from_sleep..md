---
title: "Medion MD 96630 can't resume from sleep."
date: 2011-06-29
forum: Hardware
---

### Post by Markiemannie on 2011-06-29
Hi there,
I recently reinstalled Ubuntu again after some issues with malware on other competing OSes. Unity seemed pretty noob-proof for my mom so I installed Natty with propietairy NVidia drivers.
However, Natty can't seem to resume my computer from sleep mode: when I close the lid it goes to sleep just fine (I think), but when I open the lid again the computer tries to resume, then after a second shuts down.
I used to have this problem with Lucid with Nouveau, but that was solved easily  by installing the proprietary NVidia drivers. I already did that now at Natty, however it hasn't solved the problem.
The install is pretty much a vanilla, clean install, I only installed NVidia drivers and non-free addon for Java/Flash etc. Nothing else. There are no other manual modifications made to any system files or so. All updates are applied.
Anyone who got a solution for this really annoying problem?

Medion MD96630 specs:

[LIST]
[*]Intel Core Duo T2330 (1.6ghz, 533mhz FSB)
[*]3GB DDR2 RAM
[*]Geforce 9300M G
[*]Seagate? 160gb HDD
[/LIST]
For completeness sake, the output of lspci.
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 9300M G] (rev a1)
02:00.0 Mass storage controller: Silicon Image, Inc. SiI 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
0a:00.0 Network controller: Ralink corp. RT2860

```I'll try and get last_kmsg in a moment. *Edit: doesn't seem to be there?*

Thanks in advance for your help,
Mark

---

