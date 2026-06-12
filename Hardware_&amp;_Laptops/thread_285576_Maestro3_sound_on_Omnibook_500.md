---
title: "Maestro3 sound on Omnibook 500"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by LinuxVox on 2006-10-27
Couple of days ago I swapped a 30 Gig hard drive into an Omnibook 500 from a Presarion 1247. After running from live CD to copy /etc/X11/xorg.conf to get X server to work, the only problem left was sound not working.

Here's terminal output:

jaxnvox@VoxII:~$ lspci -X
PCI:0:0:0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridgePCI:0:1:0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
PCI:0:7:0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA
PCI:0:7:1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE
PCI:0:7:2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB
PCI:0:7:3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI
PCI:0:10:0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller
PCI:0:11:0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone]
PCI:0:11:1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem
PCI:0:13:0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator
PCI:0:17:0 IDE interface: Silicon Image, Inc. PCI0648
PCI:1:0:0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x
PCI:2:0:0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface

Running P3, 700MHz w/256MB RAM.

Vox

---

