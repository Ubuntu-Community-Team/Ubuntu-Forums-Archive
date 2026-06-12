---
title: "unable to enumerate USB device"
date: 2010-12-20
forum: Hardware
---

### Post by ender4 on 2010-12-20
I have a (rather old) 1 GB LG pen drive, which I am unable to mount with either Windows or Linux.  

After plugging in the device my dmesg | tail reads:
```
[ 8354.276232] usb 6-1: device descriptor read/64, error -71
[ 8354.500203] usb 6-1: device descriptor read/64, error -71
[ 8354.716199] usb 6-1: new full speed USB device using uhci_hcd and address 32
[ 8354.836133] usb 6-1: device descriptor read/64, error -71
[ 8355.064203] usb 6-1: device descriptor read/64, error -71
[ 8355.280194] usb 6-1: new full speed USB device using uhci_hcd and address 33
[ 8355.696192] usb 6-1: device not accepting address 33, error -71
[ 8355.808171] usb 6-1: new full speed USB device using uhci_hcd and address 34
[ 8356.224157] usb 6-1: device not accepting address 34, error -71
[ 8356.224196] hub 6-0:1.0: unable to enumerate USB device on port 1

```
I have tried disabling ehci_hcd by echoing the driver numbers to unbind, but that didn't fix anything.

I suspect the drive is completely unusable, but I wanted to check here, just in case there is some way to get it working.

---

