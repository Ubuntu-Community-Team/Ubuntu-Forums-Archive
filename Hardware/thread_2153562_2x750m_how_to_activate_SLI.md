---
title: "2x750m how to activate SLI?"
date: 2013-06-11
forum: Hardware
---

### Post by grozni on 2013-06-11
I'm running Ubuntu 12.04 on Lenovo Y500 with 2x750m graphics. Second graphic is in ultrabay slot. I'm running latest 319.23 drivers. When I check Nvidia X settings both cards are listed but only one used. I tried adding --sli=on and multigpu=auto but after this X doesn't boot. When I installed Ubuntu at first it could not boot installation, after I removed second graphic all went smooth. SLI works under Windows 7. I disabled EFI I don't know if it is relevant. I tried installing various driver versions but no luck. Not sure what log should I attach so someone can trace.

---

### Post by grozni on 2013-06-18
Output of lspci:

> 00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0fe4 (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 0e1b (rev a1)
02:00.0 3D controller: NVIDIA Corporation Device 0fe4 (rev a1)
03:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 10)
04:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
05:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
05:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30)
05:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 30)
05:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 30)


3D controller: NVIDIA Corporation Device 0fe4 (rev a1) is the one I'm having issue with

---

