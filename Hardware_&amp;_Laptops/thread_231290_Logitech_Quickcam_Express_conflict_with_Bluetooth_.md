---
title: "Logitech Quickcam Express conflict with Bluetooth usb dongle."
date: 2006-08-07
forum: Hardware &amp; Laptops
---

### Post by Ziede on 2006-08-07
Help wanted:

When i connect both my usb bluetooth dongle and logitech webcam  Express it causes a conflict resulting my webcam cant be recongized in amsn and Ekiga softphone. WHen i unplug the bluetooth donglefrom my usb hub the webcam gets recongized and can be used again in Ekiga en Amsn.

During the installation of Ubuntu 6.06 DD i only had my usb mouse plugged in. After Ubuntu installed i plugged in my other usb devices. Ubuntu recongized my webcam and i did not install any other drivers.

I have two usb ports on my motherboard. The webcam is on the hub with bluetooth, printer and usb stick. My mouse is plugged in the other port.

Thanks in advance,

Zie

---

### Post by Ziede on 2006-08-12
The thing is when i connect the bluetooth i cant use the webcam. Is it possible to block the bluetooth hardware by a script? So when i need the bluetooth i can unblock using that same script. Help appreciated.
lsusb gives me with bluetooth:

daoud@daoud-desktop:~$ lsusb
Bus 001 Device 012: ID 03f0:3f11 Hewlett-Packard PSC-1315/PSC-1317
Bus 001 Device 011: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 007: ID 046d:0920 Logitech, Inc. QuickCam Express
Bus 001 Device 006: ID 0925:8866 Lakeview Research WiseGroup Ltd, MP-8866 Dual Joypad
Bus 001 Device 003: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

and without bluetooth:
Bus 001 Device 012: ID 03f0:3f11 Hewlett-Packard PSC-1315/PSC-1317
Bus 001 Device 007: ID 046d:0920 Logitech, Inc. QuickCam Express
Bus 001 Device 006: ID 0925:8866 Lakeview Research WiseGroup Ltd, MP-8866 Dual Joypad
Bus 001 Device 003: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

Hcitool dev:
Devices:
        hci0    00:10:60:A2:79:D4

P.S: lsusb says Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode).
But its an Sitecom cn-500 usb-dongle

---

### Post by Ziede on 2006-08-18
I've given up, workaround is to unplug the bluetooth. I dont use bluetooth that much. Then i can use the webcam. 


Zie.

---

