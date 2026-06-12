---
title: "Connecting to motorola v950 via usb"
date: 2009-08-11
forum: Hardware
---

### Post by tcmichals on 2009-08-11
I'm trying to connect my cell phone up via usb.. I see that the moto_modem has the support.  I cable the phone to the usb port and see the port..root@tcmichals-desktop:/# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 010: ID 22b8:2c64 Motorola PCS 
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@tcmichals-desktop:/# 
but I don't see a ttyUSB0 connection, I try and do a modprobe moto_modem  and still nothing ... the ids match so I'm lost...

---

### Post by tcmichals on 2009-08-11
Here is dmesg output and a plug unplug 
[  871.004045] usb 2-10: new full speed USB device using ohci_hcd and address 9
[  871.217419] usb 2-10: configuration #1 chosen from 1 choice
[ 1056.469849] usb 2-10: USB disconnect, address 9
[ 1058.948039] usb 2-9: new full speed USB device using ohci_hcd and address 10
[ 1059.161109] usb 2-9: configuration #1 chosen from 1 choice
[ 1966.231391] usb 2-9: USB disconnect, address 10
[ 1974.060044] usb 2-9: new full speed USB device using ohci_hcd and address 11
[ 1974.272953] usb 2-9: configuration #1 chosen from 1 choice

---

