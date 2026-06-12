---
title: "No sound coming out of Focusrite Scarlett 6i6 in UbuntuStudio 16.04"
date: 2016-08-12
forum: Hardware
---

### Post by ocellot2 on 2016-08-12
Hi,
I'm not being able to get any sound out off my Focusrite Scarlett 6i6 USB soundcard, although it seems to be recognized by system and shows up in volume control. I performed a fresh install of UbuntuStudio 16.04, having my soundcard powered-on and connected while installing. These are some command outputs that show that the soundcard is properly recognized by system:

$ lsusb 
Bus 002 Device 003: ID 046d:c050 Logitech, Inc. RX 250 Optical Mouse
**Bus 002 Device 004: ID 1235:8012 Focusrite-Novation Scarlett 6i6**
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 05ca:18c0 Ricoh Co., Ltd 
Bus 001 Device 003: ID 08ff:168f AuthenTec, Inc. AES1660 Fingerprint Sensor
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ usb-devices
T:  Bus=02 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  2
P:  Vendor=1235 ProdID=8012 Rev=02.60
S:  Manufacturer=Focusrite
S:  Product=Scarlett 6i6 USB
S:  SerialNumber=7855117D
C:  #Ifs= 6 Cfg#= 1 Atr=c0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=01(audio) Sub=01 Prot=20 Driver=snd-usb-audio
I:  If#= 1 Alt= 1 #EPs= 2 Cls=01(audio) Sub=02 Prot=20 Driver=snd-usb-audio
I:  If#= 2 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=20 Driver=snd-usb-audio
I:  If#= 3 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:  If#= 4 Alt= 0 #EPs= 2 Cls=01(audio) Sub=03 Prot=00 Driver=snd-usb-audio
I:  If#= 5 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=00 Driver=(none)

$ cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xc9400000 irq 37
** 1 [USB            ]: USB-Audio - Scarlett 6i6 USB**
**                      Focusrite Scarlett 6i6 USB at usb-0000:00:1d.0-1.2, high speed**

I've already selected my USB-sound card in volume control (pavucontrol), it shows up and apparently works (the soundbar moves when starting a sound streaming), but I'm not getting any sound out of it. I've also tried configuring QjackCtl, but I get same behaviour when selecting jack in volume control (soundbar moves, but no sound).


Any hints?
Thanks!

---

### Post by ocellot2 on 2016-08-12
Sorry, but after 2 weeks googling around without success, I've just found the solution just after posting. I've gone again through this guide: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure). It happened thay my Master 1 (Monitor) channel got muted. I opened alsamixer, selected my Focusrite Scarlett 6i6 sound card, moved to Master 1 channel, pressed 'M' and suddenly sound appeared!

---

