---
title: "Bluetooth USB adapter not found"
date: 2017-08-19
forum: Hardware
---

### Post by jamesw-6 on 2017-08-19
lsusb shows
```
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 013: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 003 Device 012: ID 0bb4:0c81 HTC (High Tech Computer Corp.) 
Bus 003 Device 005: ID 093a:2521 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 004: ID 0461:0010 Primax Electronics, Ltd HP PR1101U / Primax PMX-KPR1101U Keyboard
Bus 003 Device 003: ID 03f0:2911 Hewlett-Packard PSC 2200
Bus 003 Device 002: ID 061c:0008 Act Labs, Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth
```
gives the following
```
Linux jamie-linux 4.4.0-92-generic #115-Ubuntu SMP Thu Aug 10 09:04:33 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Kernel driver in use: rt2800pci
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 013: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 003 Device 012: ID 0bb4:0c81 HTC (High Tech Computer Corp.) 
Bus 003 Device 005: ID 093a:2521 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 004: ID 0461:0010 Primax Electronics, Ltd HP PR1101U / Primax PMX-KPR1101U Keyboard
Bus 003 Device 003: ID 03f0:2911 Hewlett-Packard PSC 2200
Bus 003 Device 002: ID 061c:0008 Act Labs, Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[   12.680104] Bluetooth: Core ver 2.21
[   12.680115] Bluetooth: HCI device and connection manager initialized
[   12.680117] Bluetooth: HCI socket layer initialized
[   12.680119] Bluetooth: L2CAP socket layer initialized
[   12.680123] Bluetooth: SCO socket layer initialized
[   27.285146] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.285148] Bluetooth: BNEP filters: protocol multicast
[   27.285150] Bluetooth: BNEP socket layer initialized
[    0.139919] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
bluetooth             520192  10 bnep,btbcm,btrtl,btusb,btintel
```

The adapter works fine under windows

I've tried blueman but no adapters are detected
Any ideas on how to get this working are greatly appreciated

---

### Post by jeremy31 on 2017-08-19
I can't find anything within the past 8 years that have been able to make that device work in Linux.  It was reported to have worked at one point.
I would replace it with an IO Gear GBU 521 as it works well in Linux and Windows and it is small- makes it easy to lose

---

