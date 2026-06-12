---
title: "SmartCard reader not working"
date: 2014-03-31
forum: Hardware
---

### Post by hotbelgo on 2014-03-31
I have a new smartcard reader, which works on a Mac, but I cannot get it recognised in Linux. When I attach it, I can do

```
$ lsusb
Bus 002 Device 007: ID 048d:1365 Integrated Technology Express, Inc. 
```

and

```
$ dmsg
[16205.981515] usb 2-5: USB disconnect, device number 6[16207.445255] usb 2-5: new high-speed USB device number 7 using ehci-pci
[16207.728014] usb 2-5: New USB device found, idVendor=048d, idProduct=1365
[16207.728021] usb 2-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[16207.728025] usb 2-5: Product: SmartCard Reader
[16207.728027] usb 2-5: Manufacturer: Generic 
[16207.728030] usb 2-5: SerialNumber: 0000000000000006

```
but that's all, pcsc_scan doesn't find anything and neither does opensc-tool --list-readers

What can I try next?

---

