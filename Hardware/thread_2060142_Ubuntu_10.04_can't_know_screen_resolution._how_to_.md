---
title: "Ubuntu 10.04 can't know screen resolution. how to fixed it ?"
date: 2012-09-19
forum: Hardware
---

### Post by sherlockwang on 2012-09-19
below is the command **lspci** information


> 
sherlock@sherlock-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b4)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 1c49 (rev 04)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1)
03:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (rev 01)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)
04:00.1 SD Host controller: Broadcom Corporation Device 16bc (rev 10)
04:00.2 System peripheral: Broadcom Corporation Device 16be (rev 10)
04:00.3 System peripheral: Broadcom Corporation Device 16bf (rev 10)
05:00.0 USB Controller: NEC Corporation Device 0194 (rev 04)



And System > Preferences > Monitors  window show "unknow" sign,displayed resolution only one option,is 1024X768(4:3),but is uncorrect.My correct displayed resolution is 1366 X 768.How to fixed it ? Some help would really be wonderful. Thanks!
PS:My system is 64 bit.And I couldn't find the xorg.conf in the x11 folder.

---

