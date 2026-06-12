---
title: "Integrated SD card reader in the laptop doesn't get detected"
date: 2007-02-05
forum: Hardware &amp; Laptops
---

### Post by 9a3eedi on 2007-02-05
Hi

My laptop has an SD card reader embedded in it. It works fine in Windows XP with no problems.. but in Linux, whenever I insert an SD card, nothing happens, and the SD card LED icon does not glow on the laptop either (It glows in windows). Apparently Linux doesnt seem to detect my SD card reader.. 

How can I fix this?

output of lspci:

```
0:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:01.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 01)
02:04.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

```

I use kubuntu 6.10 on a Centrino 1.7 x86 laptop (Fujitsu Siemens)

---

### Post by ltmon on 2007-02-05
It seems (from cursory Googling) that there is no official linux driver produced for the ENE card reader, nor have they published any specifications so that a driver can be written by the community.

My not-very-useful advice is to use a USB SD card adapter for now if you need it and to look for Ricoh, Texas Instruments or other well supported card readers in your future purchases.

---

### Post by 9a3eedi on 2007-02-06
So there's no hope for the future .______.


Well I have an SD card reader.. HAD it.. disappeared, so I had to use this :/

---

### Post by bjornolai on 2007-02-14
This might be an obvious suggestion but if your running edgy you might want to try doing: 

$ sudo setpci -s 02:04.1 4c.b=0x02  

A good thread is this one:
[http://www.ubuntuforums.org/showthread.php?t=315497](http://www.ubuntuforums.org/showthread.php?t=315497)

---

### Post by miscz on 2007-02-14
> **ltmon said:**
> It seems (from cursory Googling) that there is no official linux driver produced for the ENE card reader, nor have they published any specifications so that a driver can be written by the community.

My not-very-useful advice is to use a USB SD card adapter for now if you need it and to look for Ricoh, Texas Instruments or other well supported card readers in your future purchases.
Ummm, I wouldn't recommend Ricoh card reader, integrated one in my Asus notebook is not supported. Maybe it's just an exception, just warning ;)

---

