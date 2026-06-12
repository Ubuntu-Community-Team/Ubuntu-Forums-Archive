---
title: "Devices problems"
date: 2012-08-04
forum: Hardware
---

### Post by gipsyshadow on 2012-08-04
Hi all,

I've just put a PCMCIA USB HUB 2.0 by Kraun in my old acer notebook and it doesn't work properly: if I put a sandisk cruzer pendrive it's ok but if I put my logitech usb mouse it doesn't work!

I've another problem with my trust bluetooth usb dongle: when I put it in its led switches on but doesn't blink.

Here's my lsusb (without my mouse):

```
gipsy@acer:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 1310:0001 Roper Class 1 Bluetooth Dongle
Bus 004 Device 002: ID 0451:2036 Texas Instruments, Inc. TUSB2036 Hub
Bus 004 Device 003: ID 0483:1307 SGS Thomson Microelectronics Cytronix 6in1 Card Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

and here's is my lspci:
```
gipsy@acer:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:06.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:06.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
03:00.0 USB controller: NEC Corporation USB (rev 44)
03:00.1 USB controller: NEC Corporation USB 2.0 (rev 05)
```

I've googled and I've found this page [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids) where's listed my "Texas Instruments, Inc. TUSB2036 Hub", so I wonder if it's compatible or not with linux. Furthermore I've installed bluetooth packages but the system finds no adapters!

Can you help me please? Thanks

---

