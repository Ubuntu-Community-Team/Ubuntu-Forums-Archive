---
title: "Problems with wireless on HP 6735s (Ubuntu 9.10)"
date: 2009-12-07
forum: Hardware
---

### Post by DustBGD89 on 2009-12-07
Hello everyone! I am new on this forum, because I am not from english speaking area, but I didn`t find an answer on my local forum, so I need to ask you for a help, because it is somehow urgent.
I`ve got a laptop HP 6735s, where I`ve installed Ubuntu 9.10. First, I detected no problems, but I needed to reinstall Ubuntu for a few reasons (re-partitioning,...) and I did so.
Then, I couldn`t connect to my home wireless network. Soon, I realised that it also didn`t detect my laptop wireless adapter. I did a Live CD boot, and it also didn`t detect my wireless adapter. Then I went to Windows 7 (I have a dual boot), and wireless has perfectly worked. I made a boot from Solaris live CD, and wireless didn`t work again. Any idea what it could be?

Btw, somewhere I`ve found these commands: [B]sudo lspci
[/B]after that, I`ve got:
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4357 (rev 10)
06:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
The next command, **sudo lshw -C network **has given me:
*-network
description: Ethernet interface
product: Marvell Technology Group Ltd.
vendor: Marvell Technology Group Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 10
serial: 00:22:64:68:50:80
size: 100MB/s
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A latency=0 link=no multicast=yes port=twisted pair speed=100MB/s
resources: irq:28 memory:d3100000-d3103fff ioport:3000(size=256)
*-network
description: Network controller
product: BCM4322 802.11a/b/g/n Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:06:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=b43-pci-bridge latency=0
resources: irq:17 memory:d2000000-d2003fff

Any idea what should I do next?

---

### Post by DustBGD89 on 2009-12-07
Anyone!?

---

### Post by icek on 2009-12-19
You have to install wifi driver. System->Administration->HardwareDrivers

---

