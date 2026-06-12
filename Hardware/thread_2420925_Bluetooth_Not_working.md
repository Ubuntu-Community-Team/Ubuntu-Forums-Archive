---
title: "Bluetooth Not working"
date: 2019-06-13
forum: Hardware
---

### Post by artemis137 on 2019-06-13
Kubuntu 19.04

I keep getting the message "Bluetooth Adapter not found" when it exists. I got it working the other day when this happened, not sure what i did, but i cant get it working again at all.
using thinkpad x260

here is the outputs of rfkill, lspci and lsusb


[FONT=monospace][COLOR=#000000]0: hci0: Bluetooth[/COLOR]
        Soft blocked: no
        Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
        Soft blocked: no
        Hard blocked: no
2: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Pr
ocessor Host Bridge/DRAM Registers [8086:1904] (rev 08)
00:02.0 VGA compatible controller [0300]: Intel Corporation Skylake GT2 [HD Graphics 520
] [8086:1916] (rev 07)
00:14.0 USB controller [0c03]: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controlle
r [8086:9d2f] (rev 21)
00:14.2 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Thermal 
subsystem [8086:9d31] (rev 21)
00:16.0 Communication controller [0780]: Intel Corporation Sunrise Point-LP CSME HECI #1
 [8086:9d3a] (rev 21)
00:17.0 SATA controller [0106]: Intel Corporation Sunrise Point-LP SATA Controller [AHCI
 mode] [8086:9d03] (rev 21)
00:1c.0 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #1 [
8086:9d10] (rev f1)
00:1c.2 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #3 [
8086:9d12] (rev f1)
00:1f.0 ISA bridge [0601]: Intel Corporation Sunrise Point-LP LPC Controller [8086:9d48]
 (rev 21)
00:1f.2 Memory controller [0580]: Intel Corporation Sunrise Point-LP PMC [8086:9d21] (re
v 21)
00:1f.3 Audio device [0403]: Intel Corporation Sunrise Point-LP HD Audio [8086:9d70] (re
v 21)
00:1f.4 SMBus [0c05]: Intel Corporation Sunrise Point-LP SMBus [8086:9d23] (rev 21)
00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection I219-V [8086:1
570] (rev 21)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Car
d Reader [10ec:522a] (rev 01)
04:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04ca:7058 Lite-On Technology Corp.  
Bus 001 Device 002: ID 8087:0a2b Intel Corp.  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

[/FONT]

---

