---
title: "Can't mount or sync Noka Lumia 521 Phone."
date: 2016-01-16
forum: Hardware
---

### Post by noalternative on 2016-01-16
I can't seem to figure out how to mount a Nokia Lumia 521 Phone.  It is a T-Mobile Windows 8x phone.   I would like to share photos and music between this phone and ubuntu.  It doesn't even show it in my file manager when I hook it up with usb.  Windows 7 sees it, but I don't want to use Windows 7.  I am using Trusty.

---

### Post by Bucky Ball on 2016-01-16
Plug it in, open a terminal and:

> lsusb

Post the output here. Is your phone switched on when you plug it in? Mine needs to be. Plugging it in when off does nothing. The phone shows no signs of life.

---

### Post by noalternative on 2016-01-19
Here are the results. The phone is plugged in a turned on.  Can't parse if any of these are my phone?

> n#@tp ~ $ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b221 Chicony Electronics Co., Ltd integrated camera
Bus 001 Device 007: ID 0461:4d75 Primax Electronics, Ltd Rocketfish RF-FLBTAD Bluetooth Adapter
Bus 001 Device 006: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
Bus 001 Device 005: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
noalternative@ThinkPad-T420 ~ $ 



Can't parse whether any of these results are my phone.  I don't have a camera attached via usb.  I have a native camera on the top of the screen.  I have a bluetooth adapter on one usb and an ecig charger on another.

---

