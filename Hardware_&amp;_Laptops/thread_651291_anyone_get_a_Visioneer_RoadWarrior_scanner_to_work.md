---
title: "anyone get a Visioneer RoadWarrior scanner to work in Linux?"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by gnychis on 2007-12-27
Hi all,

I'm attempting to get a Visioneer RoadWarrior scanner to work in linux.  I have had no luck yet under Gutsy.  I have tried following the [Ubuntu scanning guide]("https://help.ubuntu.com/7.04/printing/C/scanning.html") and installed xsane and libsane-extras.

Whenever I plug in the device, it does not seem to understand it is a scanner:
```

[ 5208.968000] usb 5-5: new high speed USB device using ehci_hcd and address 7
[ 5209.104000] usb 5-5: configuration #1 chosen from 1 choice

```

System info:
```

Linux x60s 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

```

lsusb seems to recognize it as a Visioneer device:
```

gnychis@x60s:~$ lsusb 
Bus 005 Device 007: ID 04a7:0494 Visioneer 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 1199:0218 Sierra Wireless, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  

```

Here is my lspci output:
```

gnychis@x60s:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 09)
15:00.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)

```

Thanks!
George

---

### Post by linuxwizard on 2007-12-27
I don't see that model listed. Only one model shows supported. All others are unsupported. Would not count on working in linux.
[http://www.sane-project.org/sane-mfgs.html#Z-VISIONEER](http://www.sane-project.org/sane-mfgs.html#Z-VISIONEER)

Visioneer does not provide drivers for linux.
[http://support.visioneer.com/products/tools/OS/drivers.asp](http://support.visioneer.com/products/tools/OS/drivers.asp)

---

### Post by gnychis on 2007-12-27
thanks for the response, it was worth a try

---

### Post by geraldm on 2007-12-27
Gynchis:
Please run the command to attempt to identify the chipset that this scanner uses.  That may be helpful.
```

sane-find-scanner -v  -v

```

Thanks.

Gerald

---

### Post by desertdog on 2008-06-30
I also have a Visioneer Road Warrior. I opened it up and the chip is a GL842, made by Genesys Logic. This is supposedly similar to the GL841. By googling around I found out that there is software called "sane-genesys" that is incorporated into the SANE backend that works with several flatbed scanners with the GL841 chipset. Maybe some smart person can figure out how to get this to work with the Roadwarrior.

---

