---
title: "Intel Driver"
date: 2016-12-20
forum: Hardware
---

### Post by hyburn on 2016-12-20
curious if I need a custom intel driver
```

00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 9 Series Chipset Family USB xHCI Controller
00:16.0 Communication controller: Intel Corporation 9 Series Chipset Family ME Interface #1
00:1a.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 (rev d0)
00:1c.2 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 3 (rev d0)
00:1c.3 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 4 (rev d0)
00:1d.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #1
00:1f.0 ISA bridge: Intel Corporation 9 Series Chipset Family Z97 LPC Controller
00:1f.2 SATA controller: Intel Corporation 9 Series Chipset Family SATA Controller [AHCI Mode]
00:1f.3 SMBus: Intel Corporation 9 Series Chipset Family SMBus Controller
01:00.0 VGA compatible controller: NVIDIA Corporation GM206 [GeForce GTX 960] (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 0fba (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)
04:00.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 41)
```

---

### Post by ajgreeny on 2016-12-20
The simple answer is No , you don't need an intel driver, or not another one to that already being used.

Intel is generally very well supported by the generic, in kernel drivers, and your system appears to be very similar to mine which uses the standard kernel drivers.

However, I see you also have a Nvidia GeForce GTX 960 which may well need a proprietary driver which you should be able to install from the **Additional Drivers** utility which you can get to from your menu or the unity dash.

---

### Post by hyburn on 2016-12-20
thank you for the response, I have 2 options
 (not checked) "using NVIDIA binary driver -version 367057 from nvidia-367 (proprietary, tested)"

(is checked)  "using x.Org X server - Nouveau display driver from xserver-xorg-video-nouveau (open source)

**************************************************************

should I be using the first one?

---

