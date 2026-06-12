---
title: "SATA controller: Marvell Technology not showing HDD in Ubuntu"
date: 2021-03-07
forum: Hardware
---

### Post by archidis on 2021-03-07
Hi,

Fairly new to this, I've built my own custom Server based on a dell PowerEdge-T300. The disk utility manager does not show the 2 10GB HDD even though they exist on load in the BIOS screens.  I believe the SATA controller contributes to this problem. From terminal when I run lspci, I pasted what I receive below. When I pause the load screen, the card does bypass ahci.  Any insight into what I can check would be greatly appreciated.

00:00.0 Host bridge: Intel Corporation 5100 Chipset Memory Controller Hub (rev 90)
00:02.0 PCI bridge: Intel Corporation 5100 Chipset PCI Express x8 Port 2-3 (rev 90)
00:03.0 PCI bridge: Intel Corporation 5100 Chipset PCI Express x4 Port 3 (rev 90)
00:04.0 PCI bridge: Intel Corporation 5100 Chipset PCI Express x4 Port 4 (rev 90)
00:05.0 PCI bridge: Intel Corporation 5100 Chipset PCI Express x4 Port 5 (rev 90)
00:06.0 PCI bridge: Intel Corporation 5100 Chipset PCI Express x8 Port 6-7 (rev 90)
00:07.0 PCI bridge: Intel Corporation 5100 Chipset PCI Express x4 Port 7 (rev 90)
00:08.0 System peripheral: Intel Corporation 5100 Chipset DMA Engine (rev 90)
00:10.0 Host bridge: Intel Corporation 5100 Chipset FSB Registers (rev 90)
00:10.1 Host bridge: Intel Corporation 5100 Chipset FSB Registers (rev 90)
00:10.2 Host bridge: Intel Corporation 5100 Chipset FSB Registers (rev 90)
00:11.0 Host bridge: Intel Corporation 5100 Chipset Reserved Registers (rev 90)
00:13.0 Host bridge: Intel Corporation 5100 Chipset Reserved Registers (rev 90)
00:15.0 Host bridge: Intel Corporation 5100 Chipset DDR Channel 0 Registers (rev 90)
00:16.0 Host bridge: Intel Corporation 5100 Chipset DDR Channel 1 Registers (rev 90)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] (rev 02)
01:00.0 Ethernet controller: Broadcom Inc. and subsidiaries NetXtreme BCM5722 Gigabit Ethernet PCI Express
02:00.0 Ethernet controller: Broadcom Inc. and subsidiaries NetXtreme BCM5722 Gigabit Ethernet PCI Express
06:00.0 PCI bridge: ASMedia Technology Inc. Device 1806 (rev 01)
07:00.0 PCI bridge: ASMedia Technology Inc. Device 1806 (rev 01)
07:02.0 PCI bridge: ASMedia Technology Inc. Device 1806 (rev 01)
07:06.0 PCI bridge: ASMedia Technology Inc. Device 1806 (rev 01)
07:0e.0 PCI bridge: ASMedia Technology Inc. Device 1806 (rev 01)
[B]08:00.0 SATA controller: Marvell Technology Group Ltd. Device 9215 (rev 11)
0a:00.0 SATA controller: Marvell Technology Group Ltd. Device 9215 (rev 11)[/B]
0c:00.0 SCSI storage controller: Broadcom / LSI SAS1068E PCI-Express Fusion-MPT SAS (rev 08)
0e:00.0 PCI bridge: Intel Corporation 6702PXH PCI Express-to-PCI Bridge A (rev 09)
10:07.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] ES1000 (rev 02)

---

### Post by archidis on 2021-04-11
Anyone???? Really would appreciate someone's insight here?

---

