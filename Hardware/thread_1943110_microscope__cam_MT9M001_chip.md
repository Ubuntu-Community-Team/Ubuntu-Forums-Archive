---
title: "microscope  cam MT9M001 chip"
date: 2012-03-19
forum: Hardware
---

### Post by oxman on 2012-03-19
I am trying to get my usb microscope cam to work on my system76. My system does not recognize the cam when it is plugged into the USB port. I do lsusb and it is not seeing the microscope cam. I have searched far and wide to no avail. Any help is appreciated.

YJEYE01
Electron Eyepiece
Chip: 1/2" Micron MT9M001

It came with a windows driver. I haven't used windows since '96. Please don't tell me I have to do windows after all this time ;)

I did find a driver spca5xx that worked with a device that has the same chip but I am in no man's land right now on how to deal with it.

---

### Post by oxman on 2012-03-19
OK, progress (I think). My system is picking up the usb device. By doing lsusb I get:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 005: ID 0100:0010  
Bus 002 Device 003: ID 147e:1001 Upek 
Bus 002 Device 004: ID 5986:0308 Acer, Inc 

The cam is Bus 002 Device 005: ID 0100:0010  if that helps.

---

### Post by oxman on 2012-03-19
bump

---

### Post by concifederico on 2012-05-22
Hi, I have got a camera from same chip family. I do not know exactly which MT9 it is.. How did you manage to get lsusb recognize the device? Another symptom: My camera has a led, it should blink when it is connected to USB. It just do this on windows, not over Precise. By the way, mine is a Tucsen TCA5 (5 MPx).
Regards,
 
Federico

---

### Post by oxman on 2012-05-23
concifederico

I did

```

lsusb

```

Do if you want to get verbose.

```

lsusb -v

```

I tried for a couple of years to get it to work with no joy. I contacted one linux list (I think it was video4linux or something similar) and I was informed that the drivers for this chip are for Windows only. Please, if you find a solution let me know. Good luck.

---

