---
title: "Bluetooth adapter shows in dmesg but not lspci or lsusb?"
date: 2009-04-24
forum: Hardware
---

### Post by multikoor on 2009-04-24
Hey guys,

Just bought an asus eeepc 1000HE and installed Eeebuntu on it.

At the time I installed it I had bluetooth disabled via the BIOS, which I thought may have prevented the installer detecting it and installing the drivers for.

Booted up using the livecd version of Eeebuntu, and it doesn't recognise it either (even though bluetooth is now enabled in the bios)

Now the strange thing is, when i do either lspci or lsusb, there is no bluetooth adapter or anything bluetooth related shown, yet when i do:

```

$ sudo mesg | grep -i blue
[   66.404174] Bluetooth: Core ver 2.13
[   66.404530] Bluetooth: HCI device and connection manager initialized
[   66.404545] Bluetooth: HCI socket layer initialized
[   66.455830] Bluetooth: L2CAP ver 2.11
[   66.455849] Bluetooth: L2CAP socket layer initialized
[   66.510276] Bluetooth: SCO (Voice Link) ver 0.6
[   66.510296] Bluetooth: SCO socket layer initialized
[   66.600664] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   66.600686] Bluetooth: BNEP filters: protocol multicast
[   66.637865] Bluetooth: RFCOMM socket layer initialized
[   66.637917] Bluetooth: RFCOMM TTY layer initialized
[   66.637928] Bluetooth: RFCOMM ver 1.10

$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)

$ sudo lsusb
Bus 005 Device 003: ID 04f2:b071 Chicony Electronics Co., Ltd 
Bus 005 Device 002: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```I'm not quite a newbie to linux, but this is certainly beyond me, and I haven't managed to find anyone with a similar problem.

If anyone is able to think of something that may be able to fix that, that would be great :)

---

### Post by moraesgp on 2009-12-01
I have exactly the same problem. Did you ever find a solution for this?

---

### Post by edwardtilbury on 2010-03-24
Yeah same here.. Toshiba P105-S9339 Ubuntu 10.04 Beta 1 ..

lspci and lsusb have nothing that looks like bluetooth.. I have a Fujitsu Inc. thing but it has no model #'s..
edward@edward-toshiba:~$ lspci

LSPCI----

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce Go 7900 GS] (rev a1)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
0a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


--LSUSB
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 045e:074a Microsoft Corp. 
Bus 001 Device 002: ID 04c5:10f2 Fujitsu, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by unteer on 2010-03-31
I seem to be having the same problem on my Lenovo IdeaPad S9e.  Some googling determined that the standard btusb driver (which comes with most modern kernels) should be working, but still my Bluetooth device is not detected.

---

### Post by Fafler on 2010-03-31
> $ sudo mesg | grep -i blue
[   66.404174] Bluetooth: Core ver 2.13
[   66.404530] Bluetooth: HCI device and connection manager initialized
[   66.404545] Bluetooth: HCI socket layer initialized
[   66.455830] Bluetooth: L2CAP ver 2.11
[   66.455849] Bluetooth: L2CAP socket layer initialized
[   66.510276] Bluetooth: SCO (Voice Link) ver 0.6
[   66.510296] Bluetooth: SCO socket layer initialized
[   66.600664] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   66.600686] Bluetooth: BNEP filters: protocol multicast
[   66.637865] Bluetooth: RFCOMM socket layer initialized
[   66.637917] Bluetooth: RFCOMM TTY layer initialized
[   66.637928] Bluetooth: RFCOMM ver 1.10


As far as i can see, it doesn't really state that there is a a bluetooth device present, just that the bluetooth stack is present and loaded.

This is from a machine that doesn't have bluetooth:
```
fafler@hydrogen:~$ dmesg | grep -i blue
[  122.852189] Bluetooth: Core ver 2.15
[  122.852356] Bluetooth: HCI device and connection manager initialized
[  122.852359] Bluetooth: HCI socket layer initialized
[  122.872561] Bluetooth: L2CAP ver 2.14
[  122.872563] Bluetooth: L2CAP socket layer initialized
[  122.881557] Bluetooth: RFCOMM TTY layer initialized
[  122.881560] Bluetooth: RFCOMM socket layer initialized
[  122.881563] Bluetooth: RFCOMM ver 1.11
[  122.911690] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  122.911693] Bluetooth: BNEP filters: protocol multicast
[  123.013285] Bluetooth: SCO (Voice Link) ver 0.6
[  123.013288] Bluetooth: SCO socket layer initialized
fafler@hydrogen:~$
```

And this is from one that has:
```
fafler@oxygen:~$ dmesg| grep -i blue
[    0.248009] Bluetooth: Core ver 2.15
[    0.248027] Bluetooth: HCI device and connection manager initialized
[    0.248027] Bluetooth: HCI socket layer initialized
[    1.023480] Bluetooth: L2CAP ver 2.13
[    1.023482] Bluetooth: L2CAP socket layer initialized
[    1.023486] Bluetooth: SCO (Voice Link) ver 0.6
[    1.023488] Bluetooth: SCO socket layer initialized
[    1.023518] Bluetooth: RFCOMM TTY layer initialized
[    1.023523] Bluetooth: RFCOMM socket layer initialized
[    1.023525] Bluetooth: RFCOMM ver 1.11
[   20.211660] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   38.811985] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   38.811989] Bluetooth: BNEP filters: protocol multicast
[  108.735422] Bluetooth: HIDP (Human Interface Emulation) ver 1.2

```

The only difference is [   20.211660] Bluetooth: Generic Bluetooth USB driver ver 0.5, which lead me to believe that it in fact does not find your bluetooth adapter.

What output does any off you get from hcitool ident? Your bluetooth devices are probably disabled either by switch or BIOS og simply not present.

---

### Post by liju.g.chacko on 2012-09-29
On Toshiba satellite L640 for Ubuntu  12.04 (precise) 32-bit
Problem is coming with *kernel 3.2.0-24-generic-pae* but not with *kernel 3.2.0-23-generic-pae*

---

### Post by rdroberto on 2013-03-31
Same problem with:
- Acer Aspire TimelineUltra M5-481T-6642

$uname -a
Linux system 3.2.0-4-amd64 #1 SMP Debian 3.2.39-2 x86_64 GNU/Linux 
(wheezy/testing)

$hcitools dev
Devices:
	hci0	E0:06:E6:3D:DA:AA

$lspci | grep -i blue
(nothing)

$lsusb | grep -i blue
(nothing)

$ dmesg | grep -i blue
[   11.941122] Bluetooth: Core ver 2.16
[   11.941138] Bluetooth: HCI device and connection manager initialized
[   11.941140] Bluetooth: HCI socket layer initialized
[   11.941141] Bluetooth: L2CAP socket layer initialized
[   11.941145] Bluetooth: SCO socket layer initialized
[   12.120298] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   20.686947] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.686951] Bluetooth: BNEP filters: protocol multicast
[   20.980903] Bluetooth: RFCOMM TTY layer initialized
[   20.980917] Bluetooth: RFCOMM socket layer initialized
[   20.980924] Bluetooth: RFCOMM ver 1.11

---

### Post by rdroberto on 2013-03-31
Same problem with:
- Acer Aspire TimelineUltra M5-481T-6642

$uname -a
Linux system 3.2.0-4-amd64 #1 SMP Debian 3.2.39-2 x86_64 GNU/Linux 
(wheezy/testing)

$hcitools dev
Devices:
	hci0	E0:06:E6:3D:DA:AA

$lspci | grep -i blue
(nothing)

$lsusb | grep -i blue
(nothing)

$ dmesg | grep -i blue
[   11.941122] Bluetooth: Core ver 2.16
[   11.941138] Bluetooth: HCI device and connection manager initialized
[   11.941140] Bluetooth: HCI socket layer initialized
[   11.941141] Bluetooth: L2CAP socket layer initialized
[   11.941145] Bluetooth: SCO socket layer initialized
[   12.120298] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   20.686947] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.686951] Bluetooth: BNEP filters: protocol multicast
[   20.980903] Bluetooth: RFCOMM TTY layer initialized
[   20.980917] Bluetooth: RFCOMM socket layer initialized
[   20.980924] Bluetooth: RFCOMM ver 1.11

---

