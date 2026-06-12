---
title: "USB flashdisk is not recognized"
date: 2009-12-22
forum: Hardware
---

### Post by Brian88 on 2009-12-22
I have a Kingston 256MB usb flash drive containing some important datas. When I connect it to my Ubuntu 8.10 PC, it is not detected (it doesn't appear in the Nautilus), but dmesg shows me something scary:

```
[10298.287701] scsi 4:0:0:0: Device offlined - not ready after error recovery
[10298.451263] usb 2-1: new full speed USB device using ohci_hcd and address 3
[10313.627869] usb 2-1: device descriptor read/64, error -110
[10328.908487] usb 2-1: device descriptor read/64, error -110
[10329.188491] usb 2-1: new full speed USB device using ohci_hcd and address 4
[10344.365156] usb 2-1: device descriptor read/64, error -110
[10359.645747] usb 2-1: device descriptor read/64, error -110
[10359.925743] usb 2-1: new full speed USB device using ohci_hcd and address 5
[10364.946932] usb 2-1: device descriptor read/8, error -110
[10370.067924] usb 2-1: device descriptor read/8, error -110
[10370.346162] usb 2-1: new full speed USB device using ohci_hcd and address 6
[10375.367142] usb 2-1: device descriptor read/8, error -110
[10380.487267] usb 2-1: device descriptor read/8, error -110
[10380.590580] hub 2-0:1.0: unable to enumerate USB device on port 1

```

What's wrong witj my drive?

(note: currently I don't have any other OSes to test.)

---

