---
title: "Diamond VC500 help?"
date: 2019-02-23
forum: Hardware
---

### Post by pilgrimm on 2019-02-23
Hi! I have an old Diamond VC500 capture card that I'm trying to get working with my Ubuntu laptop. I'm not exactly sure how to work with it though. Google brings up a LinuxTV wiki page that's a bit confusing to read and many unanswered Ubuntu Forums topics so I'm a bit stuck.

lsusb brings up this:
```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hubBus 001 Device 007: ID 8087:0a2b Intel Corp. 
Bus 001 Device 005: ID 06cb:0081 Synaptics, Inc. 
Bus 001 Device 003: ID 13d3:5621 IMC Networks 
Bus 001 Device 021: ID 07de:2820 Diamond Multimedia VC500 Video Capture Dongle
Bus 001 Device 018: ID 174c:1153 ASMedia Technology Inc. ASM2115 SATA 6Gb/s bridge
Bus 001 Device 016: ID 0c76:161e JMTek, LLC. 
Bus 001 Device 015: ID 04f2:1459 Chicony Electronics Co., Ltd 
Bus 001 Device 014: ID 0461:4e67 Primax Electronics, Ltd 
Bus 001 Device 006: ID 0a05:7220 Unknown Manufacturer 
Bus 001 Device 012: ID 046d:082c Logitech, Inc. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
dmesg:
```
[375577.748777] usb 1-2.4: USB disconnect, device number 19[375578.740301] usb 1-2.4: new high-speed USB device number 20 using xhci_hcd
[375579.090516] usb 1-2.4: New USB device found, idVendor=07de, idProduct=2820
[375579.090523] usb 1-2.4: New USB device strings: Mfr=16, Product=32, SerialNumber=64
[375579.090528] usb 1-2.4: Product: USB Device
[375579.090532] usb 1-2.4: Manufacturer: Diamond
[375579.090535] usb 1-2.4: SerialNumber: USB Device
[375580.309246] usb 1-2.4: USB disconnect, device number 20
[375582.092272] usb 1-2.4: new high-speed USB device number 21 using xhci_hcd
[375582.457767] usb 1-2.4: New USB device found, idVendor=07de, idProduct=2820
[375582.457770] usb 1-2.4: New USB device strings: Mfr=16, Product=32, SerialNumber=64
[375582.457772] usb 1-2.4: Product: USB Device
[375582.457774] usb 1-2.4: Manufacturer: Diamond
[375582.457775] usb 1-2.4: SerialNumber: USB Device

```
Any help is appreciated! :)

---

