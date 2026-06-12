---
title: "Multitouch controller problem"
date: 2013-05-15
forum: Hardware
---

### Post by jokemach on 2013-05-15
Hi,

I've just installed Ubuntu 13.04 on a ASUS Transformer AiO 18.4". 
The multi-touch doesn't seem to work and the following message is continuously printed to syslog:
> 
[  313.268463] input: USBest Technology SiS HID Touch Controller as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/input/input308
[  313.268916] hid-multitouch 0003:0457:0817.012C: input,hiddev0,hidraw4: USB HID v1.00 Device [USBest Technology SiS HID Touch Controller] on usb-0000:00:1a.0-1.3.1/input0
[  313.309349] hid-multitouch 0003:0457:0817.012C: can't reset device, 0000:00:1a.0-1.3.1/input0, status -71
[  313.314958] hid-multitouch 0003:0457:0817.012C: can't reset device, 0000:00:1a.0-1.3.1/input0, status -71
[  313.320969] hid-multitouch 0003:0457:0817.012C: can't reset device, 0000:00:1a.0-1.3.1/input0, status -71
[  313.326957] hid-multitouch 0003:0457:0817.012C: can't reset device, 0000:00:1a.0-1.3.1/input0, status -71
[  313.332967] hid-multitouch 0003:0457:0817.012C: can't reset device, 0000:00:1a.0-1.3.1/input0, status -71
[  313.338951] hid-multitouch 0003:0457:0817.012C: can't reset device, 0000:00:1a.0-1.3.1/input0, status -71
[  313.344962] hid-multitouch 0003:0457:0817.012C: can't reset device, 0000:00:1a.0-1.3.1/input0, status -71
[  313.350951] hid-multitouch 0003:0457:0817.012C: can't reset device, 0000:00:1a.0-1.3.1/input0, status -71
[  313.356960] hid-multitouch 0003:0457:0817.012C: can't reset device, 0000:00:1a.0-1.3.1/input0, status -71
[  313.362946] hid-multitouch 0003:0457:0817.012C: can't reset device, 0000:00:1a.0-1.3.1/input0, status -71
[  313.368959] hid-multitouch 0003:0457:0817.012C: can't reset device, 0000:00:1a.0-1.3.1/input0, status -71
[  313.374943] hid-multitouch 0003:0457:0817.012C: can't reset device, 0000:00:1a.0-1.3.1/input0, status -71
[  313.380954] hid-multitouch 0003:0457:0817.012C: can't reset device, 0000:00:1a.0-1.3.1/input0, status -71
[  313.386942] hid-multitouch 0003:0457:0817.012C: can't reset device, 0000:00:1a.0-1.3.1/input0, status -71
[  313.392951] hid-multitouch 0003:0457:0817.012C: can't reset device, 0000:00:1a.0-1.3.1/input0, status -71
[  313.398938] hid-multitouch 0003:0457:0817.012C: can't reset device, 0000:00:1a.0-1.3.1/input0, status -71
[  313.404950] hid-multitouch 0003:0457:0817.012C: can't reset device, 0000:00:1a.0-1.3.1/input0, status -71
[  313.410934] hid-multitouch 0003:0457:0817.012C: can't reset device, 0000:00:1a.0-1.3.1/input0, status -71
[  313.416943] hid-multitouch 0003:0457:0817.012C: can't reset device, 0000:00:1a.0-1.3.1/input0, status -71
[  313.422934] hid-multitouch 0003:0457:0817.012C: can't reset device, 0000:00:1a.0-1.3.1/input0, status -71
[  313.428944] hid-multitouch 0003:0457:0817.012C: can't reset device, 0000:00:1a.0-1.3.1/input0, status -71
[  313.434931] hid-multitouch 0003:0457:0817.012C: can't reset device, 0000:00:1a.0-1.3.1/input0, status -71
[  313.435818] usb 1-1.3.1: USB disconnect, device number 63
[  313.646431] usb 1-1.3.1: new full-speed USB device number 64 using ehci-pci
[  313.825014] usb 1-1.3.1: not running at top speed; connect to a high speed hub
[  314.238425] usb 1-1.3.1: New USB device found, idVendor=0457, idProduct=0817
[  314.238429] usb 1-1.3.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  314.238432] usb 1-1.3.1: Product: SiS HID Touch Controller
[  314.238434] usb 1-1.3.1: Manufacturer: USBest Technology
[  314.340473] input: USBest Technology SiS HID Touch Controller as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/input/input309
[  314.340809] hid-multitouch 0003:0457:0817.012D: input,hiddev0,hidraw4: USB HID v1.00 Device [USBest Technology SiS HID Touch Controller] on usb-0000:00:1a.0-1.3.1/input0
[  314.341860] usb 1-1.3.1: USB disconnect, device number 64
[  314.642204] usb 1-1.3.1: new full-speed USB device number 65 using ehci-pci
[  314.821038] usb 1-1.3.1: not running at top speed; connect to a high speed hub
[  315.234199] usb 1-1.3.1: New USB device found, idVendor=0457, idProduct=0817
[  315.234203] usb 1-1.3.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  315.234206] usb 1-1.3.1: Product: SiS HID Touch Controller
[  315.234208] usb 1-1.3.1: Manufacturer: USBest Technology
[  315.336490] input: USBest Technology SiS HID Touch Controller as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/input/input310
[  315.336924] hid-multitouch 0003:0457:0817.012E: input,hiddev0,hidraw4: USB HID v1.00 Device [USBest Technology SiS HID Touch Controller] on usb-0000:00:1a.0-1.3.1/input0
[  315.337904] usb 1-1.3.1: USB disconnect, device number 65
[  315.649975] usb 1-1.3.1: new full-speed USB device number 66 using ehci-pci
[  315.830060] usb 1-1.3.1: not running at top speed; connect to a high speed hub
[  316.243217] usb 1-1.3.1: New USB device found, idVendor=0457, idProduct=0817
[  316.243222] usb 1-1.3.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  316.243225] usb 1-1.3.1: Product: SiS HID Touch Controller
[  316.243227] usb 1-1.3.1: Manufacturer: USBest Technology


I've tried removing the hid_multitouch module (modprobe -r) to at least stop the message from coming up, but without luck.

Any pointers?

---

### Post by gvibe06 on 2013-11-24
I know this is several months later...but I figured I would add what I did to disable the hid_multitouch kernel module from loading. This issue affects the Asus Q200E Laptop.

Edit File:   /etc/modprobe.d/blacklist.conf
Add Line:  blacklist hid_multitouch

Save and reboot....Note: This may require some patience as those error messages will print on the screen in the middle of editing the blacklist file.

Second Note: Ubuntu 13.10 still does not have a working SiS USB Touch module. Which is confusing since, the ASUS X201E is the same exact computer except it comes with Ubuntu instead of Windows 8.

---

