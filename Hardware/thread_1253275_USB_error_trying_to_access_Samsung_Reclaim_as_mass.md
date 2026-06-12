---
title: "USB error trying to access Samsung Reclaim as mass storage device"
date: 2009-08-29
forum: Hardware
---

### Post by dzoey on 2009-08-29
When I connect the Samsung Reclaim to my Ubuntu laptop (Lenevo T61p) it immediately recognizes the phone as a modem.   If I then go into the phone's Tools->Mass Storage->Connect to PC  screen, it should disconnect the modem profile and reconnect as a USB mass storage device.

The logs show the disconnect correctly, but it is unable to connect as a mass storage device with an error of:

[98716.076127] usb 4-1: USB disconnect, address 2
[98717.552089] usb 4-1: new full speed USB device using uhci_hcd and address 3
[98717.710170] usb 4-1: configuration #1 chosen from 1 choice
[98717.744121] usb-storage: probe of 4-1:1.0 failed with error -5

How should I proceed in figuring this out?  Is there a config file that needs to be updated?

---

