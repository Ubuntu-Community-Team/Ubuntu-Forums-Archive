---
title: "Qosmio F50 Bluetooth not working in 10.04"
date: 2010-05-26
forum: Hardware
---

### Post by McNuggets on 2010-05-26
I have been unable to get the Bluetooth to work on my Qosmio F50 laptop running 10.04 x86/64 . I know toshset is not compatible with this laptop for Bluetooth because it runs a phoenix bios. Anyone able to help me with this ?

uname -r
2.6.32-22-generic

lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9200M GS] (rev a1)
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
14:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
1a:00.0 Multimedia controller: Toshiba America Device 01ba (rev 01)
20:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
20:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
20:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
20:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
20:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

---

### Post by denis_dp on 2010-12-10
Have you seen this:
[http://www.linlap.com/wiki/toshiba+qosmio+f50-f55](http://www.linlap.com/wiki/toshiba+qosmio+f50-f55)

It was little bit weird and scarry for me but I decide to try. IT WORKS!!! :KS
I have Toshiba Qosmio F50-108 PQF55E-00T013G3.

---

