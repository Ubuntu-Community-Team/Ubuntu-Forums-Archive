---
title: "USB detected and delivering power"
date: 2009-09-28
forum: Hardware
---

### Post by coolbrook on 2009-09-28
...but that's just about it.  I recently discovered that my [Tyan Thunder LE-T (S2518[COLOR="White"].[/COLOR])](ftp://ftp.tyan.com/manuals/m_s2518_120.pdf) has an onbaord USB header (J80) that I can use for the front panel of my ATX case.  I hooked it up and I've tried my USB flash drive (to no avail) and I figured that I was out of luck.  For kicks, I attached a Logitech gamepad and to my surprise the turbo light lit up when I pressed the button.  Once again there appears to be a problem since I can't map it on gfceux (NES emulator) like I could on the USB ports at the back of the motherboard.

```
steven@LEONARDO:~$ lsusb
Bus 001 Device 004: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 001 Device 002: ID 0d8c:0103 C-Media Electronics, Inc. Turtle Beach Audio Advantage Micro
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

It's my belief that it's the third device detected above.  I'll love to get this working and need your help.

---

### Post by IcarusR on 2009-09-28
The third line is the internal usb hub not your gamepad, which it would appear is not recognized.

---

### Post by coolbrook on 2009-09-28
I understand that. That is what I mean.

---

### Post by coolbrook on 2009-09-29
[color="white"]1[/color]

---

### Post by coolbrook on 2009-09-30
bump

---

