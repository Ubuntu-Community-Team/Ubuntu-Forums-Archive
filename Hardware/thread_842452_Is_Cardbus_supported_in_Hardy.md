---
title: "Is Cardbus supported in Hardy ?"
date: 2008-06-27
forum: Hardware
---

### Post by Julian David Pitt on 2008-06-27
**[COLOR="Blue"]Can anyone please tell me how I can get a USB 2 card to wrk in Hardy as my old T23 laptop only has USB 1.1 which is painfully slow for anything. Thanks in advance of anyone who can be bothered to answer :)[/COLOR]**

---

### Post by lswb on 2008-06-27
I have a cheap generic USB 2.0 cardbus card, it has always "just worked" with a P3/650 going back to at Dapper at least. Is the hardy system not recognizing the card?

---

### Post by timcredible on 2008-06-27
are you saying you installed the card and it's not working?  if so, have you checked the bios to make sure the bios sees the card and it's enabled?

---

### Post by Julian David Pitt on 2008-07-01
To be honest I have no idea how to figure out if it is working or not, when I plug a USB device into it it seems to do nothing. This is what i get from a terminal:
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
02:00.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:00.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:02.0 Communication controller: Agere Systems WinModem 56k (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)
07:00.0 Ethernet controller: Belkin Unknown device 701f (rev 20)

---

### Post by lswb on 2008-07-01
I take it that what you have posted is the output of the lspci command? If the card was plugged in at that time, I don't see anything referring to it. The lines referring to usb that have Intel 82801 in them are for integrated usb ports. Try typing "lsusb" in a terminal, without the card, then again with the card. If the laptop works ok with other cardbus or pcmcia cards, the usb card is likely defective. Can you try the card in another laptop?

The good news is these cards are really cheap, probably under $10 on ebay. It's unlikely that there would be a linux compatibility problem with a cardbus usb adapter in your T23.

---

### Post by Julian David Pitt on 2008-07-03
Hi lswb
Sorry I should have said what I posted was the output of the lsusb command with the card plugged in. That is a good idea to try it in another laptop, I will do that and come back if necessary. I have a belkin wireless card in the other cardbus slot that works fine so I guess my cheap card was just too cheap to work! Thanks for your help.

---

