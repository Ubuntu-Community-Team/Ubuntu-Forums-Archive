---
title: "USB GNSS device never gets attached"
date: 2022-01-12
forum: Hardware
---

### Post by kevsterkingen on 2022-01-12
I insert my GNSS device via USB in hopes of getting a device path to read serially from it:
I do this using my raspberry Pi 4 that I intend to use as a rtk ntrip caster.

lusb gives:
```
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 1546:01a9 U-Blox AG u-blox GNSS receiver
Bus 001 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


dmesg gives:
```
[  175.728623] usb 1-1.1: new full-speed USB device number 3 using xhci_hcd
[  175.833153] usb 1-1.1: New USB device found, idVendor=1546, idProduct=01a9, bcdDevice= 1.00
[  175.833183] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  175.833196] usb 1-1.1: Product: u-blox GNSS receiver
[  175.833206] usb 1-1.1: Manufacturer: u-blox AG - [www.u-blox.com]("http://www.u-blox.com")
[  414.271561] usb 1-1.1: USB disconnect, device number 3
[  417.902463] usb 1-1.3: new full-speed USB device number 4 using xhci_hcd
[  418.006723] usb 1-1.3: New USB device found, idVendor=1546, idProduct=01a9, bcdDevice= 1.00
[  418.006752] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  418.006764] usb 1-1.3: Product: u-blox GNSS receiver
[  418.006775] usb 1-1.3: Manufacturer: u-blox AG - [www.u-blox.com]("http://www.u-blox.com")
```
After plugging it in twice in different ports. I never seem to get a attach point like /dev/ttyS0 such that I can use the port.
What is going on here? It is supposed to be just a serial communication port to my knowledge, but perhaps not?.
[B]
Edit: [/B]
I think the reason for not having it work is the ubuntu OS I am running does not have a cdc-acm driver (.ko).
I have found one for the raspberry pi under the raspberry pi / linux git. But I am not sure how to install it still. Help very much appriciated

---

