---
title: "USB Joystick not detected unknown error"
date: 2017-04-10
forum: Hardware
---

### Post by bjos5000 on 2017-04-10
Hi,

I have just started using ubuntu again after few years, and I have encountered a problem getting a usb joystick be detected properly. This a generic controller (Futuretronics Genx 500), which used to work under windows, but is not detected correctly in yakety. As per the lsusb output below the device appears to be detected correctly, but then there is an error reported from dmesg which I cannot interpret. 

lsusb:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 08bb:2704 Texas Instruments Audio Codec
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 007: ID 04b4:9393 Cypress Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

dmesg:
```
[ 7732.383489] usb 2-2: new low-speed USB device number 7 using ohci-pci
[ 7732.609594] usb 2-2: New USB device found, idVendor=04b4, idProduct=9393
[ 7732.609602] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 7732.609606] usb 2-2: Product: Futuretronics Advance USB Joystick
[ 7732.609610] usb 2-2: Manufacturer: Galy
[ 7732.630307] hid-generic 0003:04B4:9393.0007: item 0 1 0 8 parsing failed
[ 7732.630341] hid-generic: probe of 0003:04B4:9393.0007 failed with error -22
```

I do not understand the meaning of the errors "hid-generic 0003:04B4:9393.0007: item 0 1 0 8 parsing  failed" or "hid-generic: probe of 0003:04B4:9393.0007 failed with error  -22", and would appreciate if anyone could help.

Cheers,
Brendan

---

### Post by oldrocker99 on 2017-04-10
A joystick problem is best moved to Hardware.

[moved to Hardware]

---

### Post by oldrocker99 on 2017-04-10
This might be better answered in the Hardware forum.

---

### Post by bjos5000 on 2017-04-15
Hi oldrocker, no worries, but please excuse my ignorance is moving the thread something I can do or a mod?

---

### Post by jamiehennings on 2017-04-18
By the way it's a hardware related issue. You need to check all your hardware ports are working properly and the drivers are up to date because sometimes system didn't detect external device because of the outdated software and drivers.

---

### Post by deadflowr on 2017-04-18
Moved to *Hardware*.
Use the report post button in the bottom corner of the post to request a move or any other action that might need staff involvement. 
(staff action is not guaranteed)

---

