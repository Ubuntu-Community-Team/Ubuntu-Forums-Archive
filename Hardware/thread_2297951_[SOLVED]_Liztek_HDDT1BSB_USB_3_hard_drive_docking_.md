---
title: "[SOLVED] Liztek HDDT1BSB USB 3 hard drive docking station not recognized"
date: 2015-10-07
forum: Hardware
---

### Post by jamesjones01 on 2015-10-07
I bought a Liztek HDDT1BSB hard drive docking station as an easy way to transfer data from one system to another, and it has worked just fine on my computers running Ubuntu... until I tried to use it on my new system that I have Ubuntu 15.10 beta 2 running on. When the device is plugged in, connected, and powered up, lsusb shows the USB ID, [FONT=monospace][COLOR=#000000]2537:1066,[/COLOR][/FONT]but it doesn't display the maker or model, and it doesn't show a drive as connected. (The 2357:1066 ID doesn't appear when the docking station is powered down, so that has to be it.) How can I get the docking station to work?

Additional data: here's what appears to be the relevant dmesg output when I power the docking station up:

[FONT=monospace][COLOR=#000000][80563.073269] usb 2-2: new SuperSpeed USB device number 5 using xhci_hcd[/COLOR]
[80563.092801] usb 2-2: New USB device found, idVendor=2537, idProduct=1066
[80563.092807] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[80563.093390] usb-storage 2-2:1.0: USB Mass Storage device detected

[/FONT]so it is detecting it as a mass storage device, but for some reason it's not mounting the drive. Better check my preferences.

SOLVED: must properly insert drive. It works fine.

---

