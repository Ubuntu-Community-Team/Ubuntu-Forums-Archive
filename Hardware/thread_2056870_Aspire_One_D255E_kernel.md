---
title: "Aspire One D255E kernel"
date: 2012-09-12
forum: Hardware
---

### Post by enriquelira on 2012-09-12
Hello, I bring a kernel compiled for Acer Aspire One D255E that is the team that I have now, weighs only 6.57 Mb all devices are working properly, but even this "testing stage", to some drivers that are not of this model, but did my best to remove those not needed. Hopefully I can "clean" construction more specifically for this netbook and reduce the size of the nucleus. The kernel version is 3.5.3 and this is the information from the computer using lspci:

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet (rev c1)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)


paulo@equipo:~$ lsusb
Bus 001 Device 002: ID 064e:d214 Suyin Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Download: [http://ubuntuone.com/7mBKRYTi1IAdArw8wD54DA]("linux-image-3.5.3-aao-d255e-netbook_3.5.3-aao-d255e-netbook-10.00.Custom_i386.deb")

---

### Post by cariboo on 2012-10-21
Moved to Hardware, as it doesn't meet the Toots & Tips criteria

---

