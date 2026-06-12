---
title: "Terra mobile 1542"
date: 2018-05-24
forum: Hardware
---

### Post by m.banu94 on 2018-05-24
Hello I installed ubuntu 16.04 on the aformentioned laptop but its not recognized as a laptop, no battery shown no display control, no nothing...please help

lspci shows this:
```
00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 07)00:02.0 VGA compatible controller: Intel Corporation Sky Lake Integrated Graphics (rev 06)
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-H Thermal subsystem (rev 31)
00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
00:17.0 SATA controller: Intel Corporation Sunrise Point-H SATA controller [AHCI mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #3 (rev f1)
00:1c.3 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #4 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #6 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (2) I219-V (rev 31)
01:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)

```

lsusb shows this:
```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:0a2b Intel Corp. 
Bus 001 Device 002: ID 058f:9540 Alcor Micro Corp. AU9540 Smartcard Reader
Bus 001 Device 006: ID 1c7a:0603 LighTuning Technology Inc. 
Bus 001 Device 005: ID 04f2:b59e Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 1ea7:0066  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by mörgæs on 2018-05-25
New hardware is better off with new software. I suggest a fresh install (no upgrades) of 18.04.

---

