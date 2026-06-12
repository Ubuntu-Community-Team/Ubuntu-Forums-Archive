---
title: "Wifi Trouble on ubuntu 10.4 for Gateway MX8741"
date: 2011-01-18
forum: Hardware
---

### Post by CGomez on 2011-01-18
I have a small problem I could use some help with I have tried all possible solutions I can't find to make my wifi connect I have tried WPA and WEP set ups I can see my router but when I try to connect, it times out after a few min and comes back with the password screen to access the encrypted network. I have checked Terminal to see if it was listed and I cant find it listed.

ike@mike-laptop:~$ sudo apt-get install bcmwl-kernel-source
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mike@mike-laptop:~$ sudo lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
03:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 02)
03:09.0 CardBus bridge [0607]: Texas Instruments PCIxx12 CardBus Controller [104c:8039]
03:09.1 Fire Wire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
03:09.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]

All hardware is listed but my wifi card is not if I go into Hardware Drivers I have one item that shows up propriarity drivers are being used to make this computer work properly

The Smart Link modem daemon is the application part of the driver for recent modems produced by Smart Link Ltd.

This package replaces (along with hardware access drivers) the old driver generation (2.7.x) which consisted of kernel modules only.

It needs a kernel driver to access the hardware. This can be either recent ALSA (shipped with a newer kernel (>=2.6.4) with ALSA support and snd-intel8x0m module) which is sufficient for basic operation and data/Internet connection, or the Smart Link kernel driver which is provided by separate packages which you can build using the source from the sl-modem-source package.

This driver enables the usage of many software modems, as commonly found in laptops.

If this driver is not enabled, you will not be able to use your modem.

I think this may just be my dial up modem but I'm new to Ubuntu and I'm not sure quite what to do.

My Wifi card i belive is a broadcom 4000 series

---

