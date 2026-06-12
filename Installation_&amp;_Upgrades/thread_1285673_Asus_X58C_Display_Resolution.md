---
title: "Asus X58C Display Resolution"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by Neil Purling on 2009-10-08
The Asus is my father's laptop. I installed Ubuntu 8.10 on it last night.
I have a display resolution issue. When I was setting up Evolution not all of the boxes were visible. I looked at Screen Resolution  in System> Preferences.
The display was represented as "Unknown" and showed resolution of 800x600 or 640x480 (4:3 ratio).
When I installed Ubuntu from the very same CD onto my own Compaq V5214ea it showed the screen to be laptop 15" and the aspect ratio 16:10. 
How can I remedy this?
Setting up Evolution was a pain in the proverbial as the buttons at the bottoms of the boxes were invisible.

---

### Post by Neil Purling on 2009-10-08
Asus X58C display problem.
I need 16:10 aspect ratio for the laptop screen.
neil@pete-laptop:~$ xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  


neil@pete-laptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0d.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
00:0d.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
00:0d.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 09)
00:0d.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev ff)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)



I have the same version on a Compaq laptop. The installation worked with no trouble there.
On the Asus the laptop display has not been detected, it just says "unknown".

---

### Post by michael.wayne on 2010-01-22
> **Neil Purling said:**
> Asus X58C display problem.
I need 16:10 aspect ratio for the laptop screen.
neil@pete-laptop:~$ xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  


neil@pete-laptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0d.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
00:0d.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
00:0d.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 09)
00:0d.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev ff)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)



I have the same version on a Compaq laptop. The installation worked with no trouble there.
On the Asus the laptop display has not been detected, it just says "unknown".



I have the EXACT same problem, someone please help! Note: I am using Karmic Koala, 9.10

---

