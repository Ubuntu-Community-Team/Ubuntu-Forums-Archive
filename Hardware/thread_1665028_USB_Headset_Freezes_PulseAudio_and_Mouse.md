---
title: "USB Headset Freezes PulseAudio and Mouse"
date: 2011-01-11
forum: Hardware
---

### Post by c_plus_plus on 2011-01-11
I own a Sound Blaster Arena Surround headset. I had it successfully working with my computer that had an Athalon 64 x2 and an ATI chipset motherboard. I recently built a new desktop that has a Phenom II x4 and an nVidia chipset. When I plug my headset in to the computer and switch to it with either the Sound Preferences or the PulseAudio volume control, I can hear sound out of it for a short time, but after that, the sound stops, and PulseAudio becomes unresponsive (applications complain they can't connect). After this, my usb mouse becomes unresponsive, and I have to use the keyboard to open a terminal and restart the computer in order to regain control. I have noticed that lsusb is unresponsive while this issue is occupying. I am uncertain how to determine what portions of what logs pertain to the problem at hand, and I will be glad to provide any additional information as needed.

Ubuntu versions:
The computer with which the headset worked was running 10.04. Originally, when I upgraded, I just moved the hard drives over, so I still had 10.04 when I first noticed the problem. Thinking the problem was caused by meerly caused by just moving the hard drives, I installed a fresh copy of 10.10 to try, but the problem still persists.

Here is some information, more will be edited in later.

lspci:
```
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
02:00.0 PCI bridge: nVidia Corporation NF200 PCIe 2.0 switch for mainboards (rev a2)
03:00.0 PCI bridge: nVidia Corporation NF200 PCIe 2.0 switch for mainboards (rev a2)
03:02.0 PCI bridge: nVidia Corporation NF200 PCIe 2.0 switch for mainboards (rev a2)
04:00.0 VGA compatible controller: nVidia Corporation Device 0e23 (rev a1)
04:00.1 Audio device: nVidia Corporation GF104 High Definition Audio Controller (rev a1)
```


This issue seems to be related to this forum post: [http://ubuntuforums.org/showthread.php?t=1399229](http://ubuntuforums.org/showthread.php?t=1399229)

None of the suggestions in the former thread are helpful, as I am certain this headset can work with different hardware in Ubuntu.

Also, I am uncertain, but this bug may also be related: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/627862](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/627862)

---

### Post by emilsit on 2012-01-20
I am having a similar problem with a Sennheiser OfficeRunner wireless headset and a wired USB mouse.  When I connect the wireless headset, the left mouse button fails to work. When I disconnect the wireless headset, the mouse returns to normal.

This is with Ubuntu 10.04.3 LTS.

$ uname -a
Linux sit-desktop 2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:32:42 UTC 2011 x86_64 GNU/Linux

$ lsusb
Bus 008 Device 004: ID 046d:c05a Logitech, Inc. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 413c:2107 Dell Computer Corp. 
Bus 007 Device 002: ID 1395:740a Sennheiser Communications 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ lspci
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 22)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 22)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 22)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 22)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 22)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 22)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 22)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
02:00.0 VGA compatible controller: ATI Technologies Inc RV620 [FirePro 2260]
05:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5761 Gigabit Ethernet PCIe (rev 10)

---

### Post by c_plus_plus on 2012-01-21
I believe you have a different problem. My problem continued after unpluging my headset. The computer would eventually become unresponsive even without the headset plugged in. The solution I found for my problem was to install a usb pci card and only use those ports for the USB headset. There seems to be some problem between linux, the chipset, and the usb headset. If you want, you can try a similar solution, but, like I said. Your problem seems to be of a slightly different nature.

---

