---
title: "Heavy problems with Intel video card / Mobile Intel GMA 4500M"
date: 2010-04-26
forum: Hardware
---

### Post by Neo¹ on 2010-04-26
Hi everybody,

my old is died few days ago and I had to buy a new one. 
Until then I had always computers with NVidia video cards and never had any problems with these. This one my new computer has a an Intel video card.
It's called Mobile Intel GMA 4500M.

My problem is that the 2D support is terrible. I'm using Kubuntu 9.10 with KDE 4.4.2 and it is almost impossible to work this computer.
If I scroll in firefox or eclipse I can almost see any single frame of the animation.

It does not matter if I switch the desktop effects on or off.

Does anyone know if there is some possibility to improve the performance of my desktop?

Here some details:

```

~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Multimedia controller: ATI Technologies Inc Device ac12
04:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)
04:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
04:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

```

hwinfo: [http://radek.suski.eu/tmp/hw](http://radek.suski.eu/tmp/hw)

any help very appreciated :)

Thanks in advance,
Radek

PS: Strange thing is; I just checked Fedora Core 12 to compare and it seems to work much better :(

---

