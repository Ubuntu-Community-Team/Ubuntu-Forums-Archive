---
title: "libretto u100 usb port inactive"
date: 2010-02-13
forum: Hardware
---

### Post by alamue on 2010-02-13
i've been amazingly happy with ubuntu. 

my problem is that my tiny second hand laptop has 2 usb ports... and only one works. and it won't allow for a usb hub to expand it.

when attaching a device to the dead port dmesg retuns
[81125.448202] usb 4-2: new full speed USB device using uhci_hcd and address 15
[81125.871566] usb 4-2: device not accepting address 15, error -71
[81125.871602] hub 4-0:1.0: unable to enumerate USB device on port 2

and lsusb returns 
Bus 004 Device 011: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

i poked around a bit and couldn't find much. 

any help appreciated

---

