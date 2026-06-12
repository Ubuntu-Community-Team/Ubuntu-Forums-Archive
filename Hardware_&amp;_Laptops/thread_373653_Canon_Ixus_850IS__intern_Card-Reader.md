---
title: "Canon Ixus 850IS / intern Card-Reader"
date: 2007-03-01
forum: Hardware &amp; Laptops
---

### Post by lanort on 2007-03-01
Hi. I am new to ubuntu and now have troubles with my new camera (Canon IXUS 850IS) and the intern card reader. (My old Canon PowerShot S30 worked fine :D )
The intern card reader also does not work. I think it completly does not work because not even the LED blinks.

[Link: My hardware per lshw](http://www.divshare.com/download/172303-cd6)

If I use the "Kamera importieren"-Dialog (german) I think it would be "import camera" or so in english (If I plug in a camera) the following error rises:
[img]http://img110.imageshack.us/img110/6769/bildschirmfotophotosimpti9.png[/img]
digiKam also did not work

Maybe that helps?
```
guru@guru-desktop:~$ lsusb
Bus 005 Device 009: ID 04a9:3136 Canon, Inc. 
Bus 005 Device 008: ID 0bc7:0006 X10 Wireless Technology, Inc. 
Bus 005 Device 006: ID 0dbf:9001 Quik Tech Solutions 
Bus 005 Device 007: ID 148f:2570 Ralink Technology, Corp. 802.11g WiFi
Bus 005 Device 003: ID 0d8c:5200 C-Media Electronics, Inc. 
Bus 005 Device 002: ID 05e3:0606 Genesys Logic, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 04f2:0420 Chicony Electronics Co., Ltd 
Bus 003 Device 003: ID 045e:001e Microsoft Corp. IntelliMouse Explorer
Bus 003 Device 001: ID 0000:0000  
guru@guru-desktop:~$
``` 

```
guru@guru-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub (rev 81)
00:01.0 PCI bridge: Intel Corporation 945G/GZ/P/PL Express PCI Express Root Port (rev 81)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0147 (rev a2)
02:01.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:04.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
02:05.0 Communication controller: Agere Systems Unknown device 0620

```

Hope there is somebody out who knows an answer [-o<

---

### Post by lanort on 2007-03-05
Nobody an idea?

---

### Post by lanort on 2007-03-11
Solved :popcorn:  

Thanks to flynn @ [http://www.ubuntu-forum.de/thread.php?postid=108805#post108805](http://www.ubuntu-forum.de/thread.php?postid=108805#post108805)

---

