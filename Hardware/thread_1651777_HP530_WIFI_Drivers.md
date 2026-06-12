---
title: "HP530 WIFI Drivers"
date: 2010-12-23
forum: Hardware
---

### Post by theoq on 2010-12-23
Hi!
 I finally achieved to install ubuntu (9.10) as the 10.04 CD did not allow me to install it. However, now I can't use my WIFI as I suppose I don't have the drivers needed for my antenna. I would like to know how could I get them and start using my WIFI. Thanks
PS, It's not that I can't connect to a Wifi Network, but that I can't find any network

---

### Post by frustratednerd on 2010-12-23
Go into terminal and type:

> lspci

and post the output of it please.

---

### Post by fluxmeister on 2011-12-25
I've got the same problem,any help please?
thank you in advance.
tec.spec:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 01)
10:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

---

