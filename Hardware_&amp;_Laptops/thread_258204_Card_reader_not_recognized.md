---
title: "Card reader not recognized"
date: 2006-09-15
forum: Hardware &amp; Laptops
---

### Post by isTHEr3mOr3 on 2006-09-15
Hi, 

I've got a Medion MD44200 with build in card reader. When I insert a 1 GB SD card nothing happens. 

Output of lspci gives this line:

0000:02:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated Flash Media Controller

So I guess it could see something. I've read on a forum (about a jear ago) that a guy managed to get it working. Wish I knew how :wink: 

Full lspci output:

0000:00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
0000:00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller ( rev 21)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EH CI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridg e (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller ( rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus  Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH 4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97  Modem Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Rad eon 9600 M10]
0000:02:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:02:04.1 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:02:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Ho st Controller
0000:02:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated Flash Media Controller
0000:02:05.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (re v 02)
0000:02:06.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)

---

