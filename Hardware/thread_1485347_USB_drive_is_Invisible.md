---
title: "USB drive is Invisible"
date: 2010-05-16
forum: Hardware
---

### Post by David Vincent-Jones on 2010-05-16
My camera interfaces the system (10.04) through a USB port.

On earlier OS versions the camera disk was always visible on my 'Places' but with the latest version the camera (disk) is invisible. No signs of it /Media either.

How do I get my data in the camera to show?

---

### Post by Crafty Kisses on 2010-05-17
What does the following bring back?
```
lsusb
```

---

### Post by David Vincent-Jones on 2010-05-17
The problem appears to lie in Digikam. The system does now see the camera and I can import images through F-Spot.

Bus 001 Device 017: ID 04a9:319b Canon, Inc. 
Bus 001 Device 005: ID 17ef:1004 Lenovo 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by David Vincent-Jones on 2010-05-17
Interesting development:

As soon as I try to import through Digikam the 'Canon' line from lsusb disappears and the camera icon drops from the screen.

---

