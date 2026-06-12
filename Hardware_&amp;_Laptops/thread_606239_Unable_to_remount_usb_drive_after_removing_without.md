---
title: "Unable to remount usb drive after removing without unmounting"
date: 2007-11-07
forum: Hardware &amp; Laptops
---

### Post by Roonaldo_7 on 2007-11-07
Hi,

I accidentally pulled out my usb drive without first unmounting it. Now, when i connect it, Ubuntu (Feisty) does not even recognize it. Same thing happens on Windows. 

dmesg | tail : 
```
[ 1061.408000] usbcore: registered new interface driver libusual
[ 1061.424000] Initializing USB Mass Storage driver...
[ 1061.424000] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1061.424000] usbcore: registered new interface driver usb-storage
[ 1061.424000] USB Mass Storage support registered.
[ 1061.424000] usb-storage: device found at 3
[ 1061.424000] usb-storage: waiting for device to settle before scanning
[ 1066.424000] usb-storage: device scan complete
[ 1072.036000] usb 5-3: reset high speed USB device using ehci_hcd and address 3
[ 1073.148000] usb 5-3: device descriptor read/64, error -71
```

Has the hard drive failed? Is there anyway I can recover the data on the drive.

---

