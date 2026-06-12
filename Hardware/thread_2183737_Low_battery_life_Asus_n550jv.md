---
title: "Low battery life Asus n550jv"
date: 2013-10-26
forum: Hardware
---

### Post by Gronibar on 2013-10-26
Hi ! I just installed Ubuntu 13.04 alongside Windows 8. I noticed that  my battery life is really short when booting on Ubuntu : about 2h,  whereas it lasts like 4-5 hours on Windows. I checked for drivers but  the proprietary driver tab is empty. Any ideas about what I could do to  improve this ?

Here is some lscpu/pci results if that's any help: 
> 
00:00.0 Host bridge: Intel Corporation Haswell DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Haswell PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Haswell Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Haswell HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation Lynx Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Lynx Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point PCI Express Root Port #1 (rev d4)
00:1c.1 PCI bridge: Intel Corporation Lynx Point PCI Express Root Port #2 (rev d4)
00:1c.2 PCI bridge: Intel Corporation Lynx Point PCI Express Root Port #3 (rev d4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point PCI Express Root Port #4 (rev d4)
00:1d.0 USB controller: Intel Corporation Lynx Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point 6-port SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point SMBus Controller (rev 04)
01:00.0 3D controller: NVIDIA Corporation GK107M [GeForce GT 750M] (rev a1)
04:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 0c)

> 
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                8
On-line CPU(s) list:   0-7
Thread(s) per core:    2
Core(s) per socket:    4
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 60
Stepping:              3
CPU MHz:               800.000
BogoMIPS:              4789.20
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              6144K
NUMA node0 CPU(s):     0-7



Thank you in advance !

---

### Post by Yellow Pasque on 2013-10-26
```
00:02.0 VGA compatible controller: Intel Corporation Haswell Integrated Graphics Controller
01:00.0 3D controller: NVIDIA Corporation GK107M [GeForce GT 750M]
```

Install Bumblebee to turn off nvidia GPU when not in use: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

