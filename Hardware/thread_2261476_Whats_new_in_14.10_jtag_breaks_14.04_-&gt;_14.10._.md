---
title: "Whats new in 14.10? jtag breaks 14.04 -&gt; 14.10. udev?"
date: 2015-01-19
forum: Hardware
---

### Post by anton-fosselius on 2015-01-19
I need some help/pointers as to what can have broken, i am trying to get my P&E Jtag to work in ubuntu 14.10, it works in ubuntu 14.04, but it brakes for 14.10. What can have caused this?

Same udev rulses and lsusb/dmesg output in both 14.10 and 14.04. Is there anything else i can check?

udev rule:
ATTR{idVendor}=="15a2", ATTR{idProduct}=="0035", MODE:="0666"
ATTR{idVendor}=="15a2", ATTR{idProduct}=="0042", MODE:="0666"
ATTR{idVendor}=="15a2", ATTR{idProduct}=="0058", MODE:="0666"
ATTR{idVendor}=="15a2", ATTR{idProduct}=="005e", MODE:="0666"
ATTR{idVendor}=="15a2", ATTR{idProduct}=="005f", MODE:="0666"
ATTR{idVendor}=="1357", MODE:="0666"

lsusb:
Bus 002 Device 015: ID 1357:0503 P&E Microcomputer Systems USB-ML-12 HCS08/HCS12 Multilinkdmesg:
[10404.517945] usb 2-2: USB disconnect, device number 14
[10406.059627] usb 2-2: new high-speed USB device number 15 using xhci_hcd
[10406.188275] usb 2-2: New USB device found, idVendor=1357, idProduct=0503
[10406.188285] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[10406.188289] usb 2-2: Product: USB-ML-ARM (FS) Rev B
[10406.188293] usb 2-2: Manufacturer: P&E Microcomputer Systems
[10406.188297] usb 2-2: SerialNumber: PE5655845

---

