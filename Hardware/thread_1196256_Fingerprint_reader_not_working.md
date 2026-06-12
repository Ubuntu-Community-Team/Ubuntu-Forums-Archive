---
title: "Fingerprint reader not working"
date: 2009-06-24
forum: Hardware
---

### Post by andreselsuave on 2009-06-24
Hi there!

I own an hp8710p laptop, which comes with this fingerprint sensor:

AuthenTec, Inc. AES2501 Fingerprint Sensor

I tried to make it work with thinkfinger, but to no sucess. Apparently, thinkfinger only works with some laptops (lenovo, toshiba...). Anyone has any idea ? Thanks a lot in advance.

andreselsuave

---

### Post by CdK1 on 2009-06-25
copy to lspci -vv

---

### Post by andreselsuave on 2009-06-26
the fingerprint reader does not appear when I do lspci -vv
```
andreselsuave@infectedmushroom:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:03.0 Communication controller: Intel Corporation Mobile PM965/GM965 MEI Controller (rev 0c)
00:03.2 IDE interface: Intel Corporation Mobile PM965/GM965 PT IDER Controller (rev 0c)
00:03.3 Serial controller: Intel Corporation Mobile PM965/GM965 KT Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 320M (rev a1)
02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 03)
02:06.3 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)
02:06.4 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
02:06.5 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 10)
02:06.6 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 10)
10:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

```
 , it appears with lsusb -v 
```
andreselsuave@infectedmushroom:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 047d:1042 Kensington 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**_Bus 004 Device 003: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor_**
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by andreselsuave on 2009-06-26
Ok, I can get the fingerprint sensor to work with fprint-demo :D:D

It detects the Authentec device, stores my fingerprints and matches them correctly. How can I do now to use my fingerprints to authenticate on my machine¿?
thanks a lot

---

### Post by CdK1 on 2009-06-26
Look this:

[http://ubuntuforums.org/showthread.php?t=760018](http://ubuntuforums.org/showthread.php?t=760018)

---

### Post by andreselsuave on 2009-06-26
Hi there ! 

Thanks a lot. Yeah, I found that thread like an hour ago and worked perfectly, ^_^ I was going to post a link to it and say it's solved. well u did it first :D 

Thanks a lot. I will mark the thread as solved

Edit: Can't find the mark as solved option. Is it because it can't be done anymore or something?

---

