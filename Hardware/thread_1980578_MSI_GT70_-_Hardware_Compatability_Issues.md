---
title: "MSI GT70 - Hardware Compatability Issues"
date: 2012-05-15
forum: Hardware
---

### Post by MSUdom5 on 2012-05-15
I just bought an MSI GT70 and installed Ubuntu 12.04. Ubuntu doesn't seem to recognize the wired network controller. 

```
lspci
```returns:

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1c.4 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 5 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1213 (rev a1)
02:00.0 Ethernet controller: Atheros Communications Inc. Device e091 (rev 13)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
04:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
```I can't find any information on the "Atheros Communications Inc. Device e091". I'm hoping someone can point me in the right direction.

Thanks in advance,
MSUdom5

---

