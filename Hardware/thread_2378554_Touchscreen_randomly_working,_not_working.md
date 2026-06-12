---
title: "Touchscreen randomly working, not working"
date: 2017-11-24
forum: Hardware
---

### Post by satan3 on 2017-11-24
My touchscreen intermittently works on my Dell Inspiron 7537, mostly   not. It generally is not detected on bootup, but only when the  computer  resumes after suspend. 

When it is detected (after suspend)  lsusb produces:

```
Bus 002 Device 010: ID 04f3:0201 Elan Microelectronics Corp. Touchscreen
```

Here's output from dmesg that might be helpful, i'm not sure what it means:

```
[12066.321322] usb 2-7: Device not responding to setup address.
[12066.529353] usb 2-7: Device not responding to setup address.
[12066.737096] usb 2-7: device not accepting address 64, error -71
[12066.737157] usb usb2-port7: unable to enumerate USB device                                                                                                                                  
[12072.921194] usb 2-7: new full-speed USB device number 65 using xhci_hcd
[12078.238349] usb 2-7: New USB device found, idVendor=04f3, idProduct=0201
[12078.238353] usb 2-7: New USB device strings: Mfr=4, Product=14, SerialNumber=0
[12078.238355] usb 2-7: Product: Touchscreen
[12078.238357] usb 2-7: Manufacturer: ELAN
[12078.248271] input: ELAN Touchscreen as /devices/pci0000:00/0000:00:14.0/usb2/2-7/2-7:1.0/0003:04F3:0201.0007/input/input39
[12078.248764] hid-multitouch 0003:04F3:0201.0007:  input,hiddev0,hidraw0: USB HID v1.10 Device [ELAN Touchscreen] on  usb-0000:00:14.0-7/input0
[12206.688765] usb 2-7: reset full-speed USB device number 65 using xhci_hcd
[12211.988422] usb 2-7: device descriptor read/64, error -110
[12212.216526] usb 2-7: device descriptor read/64, error -71
[12212.444408] usb 2-7: reset full-speed USB device number 65 using xhci_hcd
[12212.564453] usb 2-7: device descriptor read/64, error -71
[12212.792460] usb 2-7: device descriptor read/64, error -71
[12213.020418] usb 2-7: reset full-speed USB device number 65 using xhci_hcd
[12213.020619] usb 2-7: Device not responding to setup address.
[12213.228624] usb 2-7: Device not responding to setup address.
[12213.436379] usb 2-7: device not accepting address 65, error -71
[12213.556394] usb 2-7: reset full-speed USB device number 65 using xhci_hcd
[12213.556582] usb 2-7: Device not responding to setup address.
[12213.764606] usb 2-7: Device not responding to setup address.
[12213.972420] usb 2-7: device not accepting address 65, error -71
[12213.972501] usb 2-7: USB disconnect, device number 65
[12214.292362] usb 2-7: new full-speed USB device number 66 using xhci_hcd
[12214.412382] usb 2-7: device descriptor read/64, error -71
[12214.644405] usb 2-7: device descriptor read/64, error -71
[12214.872380] usb 2-7: new full-speed USB device number 67 using xhci_hcd
[12214.992373] usb 2-7: device descriptor read/64, error -71
[12215.220398] usb 2-7: device descriptor read/64, error -71
[12215.448371] usb 2-7: new full-speed USB device number 68 using xhci_hcd
[12215.448579] usb 2-7: Device not responding to setup address.
[12215.656548] usb 2-7: Device not responding to setup address.
[12215.864407] usb 2-7: device not accepting address 68, error -71
[12215.984466] usb 2-7: new full-speed USB device number 69 using xhci_hcd
[12215.984740] usb 2-7: Device not responding to setup address.
[12216.192737] usb 2-7: Device not responding to setup address.
[12216.400385] usb 2-7: device not accepting address 69, error -71
[12216.400432] usb usb2-port7: unable to enumerate USB device
```

Booting from a LiveUSB, the touchscreen works out of the box on  Ubuntu  Gnome, Ubuntu 16.04.03 LTS, but not on Ubuntu 17.10, KDE Neon  (any  version the last couple of years) or Kubuntu. I've been having  this  problem for a few years now i've searched for answers on here and  other  websites but to no avail. Is there anyone out there who could  help?

---

