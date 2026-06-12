---
title: "Mutliple Sound card Problem"
date: 2007-10-06
forum: Hardware &amp; Laptops
---

### Post by SpaceTeddy on 2007-10-06
Hi Folks,

i've been hitting the wall with this problem for two days now and don't seem to be able to fix it.
My Laptop (Samsund X10) has an inbuild soundcard. Unforteunatly, the quality comming out of it is rather... bad, since the headphones-jack interferes with the harddrive and i get all scrachy noises.

so i bought myself a usb stick sound card... plugged it in, and voila, it got detected and i can choose it in the configuration. I also can listen to music if i use xmms and select that soundcard specificially. But all other applications always default to the onboard soundcard - which is driving me bananas

i've used the gnome setting for the soundcard, i've used asoundconf to set the default soundcard, i've even blacklisted the module for my internal soundcard and hoped that gnome will then default to the usb one -. NO LUCK .
NOTE: i cannot disable the soundcard in the bios

i should say, tho, that the initial music from the x-server is played via the usb card - just everything in a (i have tried this with other users aswell) session is not defaulting to it.

here is some information about my system:

$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 001 Device 002: ID 0f62:1

$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
02:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:03.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:03.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
02:05.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:07.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
001 Acrox Technologies Co., Ltd 
Bus 001 Device 001: ID 0000:0000  

$ asoundconf list
Names of available sound cards:
I82801DBICH4
default

$ aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: I82801DBICH4 [Intel 82801DB-ICH4], Gerät 0: Intel ICH [Intel 82801DB-ICH4]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: I82801DBICH4 [Intel 82801DB-ICH4], Gerät 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 1: default [C-Media USB Headphone Set  ], Gerät 0: USB Audio [USB Audio]
  Untergeordnete Geräte: 0/1
  Untergeordnetes Gerät '0: subdevice #0

if anybody could tell me how to make the usb sound my default - really - you'd be my hero for at least a year.

thanks a lots, folks

---

