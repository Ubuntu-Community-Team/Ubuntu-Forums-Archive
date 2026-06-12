---
title: "Not detecting a USB scanner in Hardy"
date: 2008-10-10
forum: Hardware
---

### Post by LewisTM on 2008-10-10
I have recently installed Kubuntu Hardy 8.04 on a Core2Duo System, 64 bit. I attempted to connect to my Microtek 4800 USB scanner but, as experienced in [this thread]("http://ubuntuforums.org/showthread.php?t=783983"), I got a permission error, so I did as suggested and compiled the old 1.0.15 backend sm3480 driver to replace 1.0.19 which is broken. 

That didn't work for some reason, plus now xsane and sane-find-scanner cannot find any scanner connected to the system. 

Reinstalling the sane-related packages and the libsane1.0.19 backend didn't improve things.
Using lsusb or the KInfocenter, I can clearly see the scanner at Bus 005:002, so it's there and powered.

Not sure if this is related to my problem or to the way recent Ubuntu releases work, but I find no scanner.o module or /dev/scanner or dev/usb/scanner node anywhere on my system.

I'm at a loss. Anybody have a clue?

---

### Post by cariboo on 2008-10-10
It would help if you included the make and model as well as the proper bus id numbers, the numbers you included are not correct. the bus id numbers usually consist of to sets of 4 numbers.

Jim

---

### Post by LewisTM on 2008-10-11
Okay, here's my lsusb output:
> Bus 004 Device 005: ID 413c:5602 Dell Computer Corp.
Bus 004 Device 004: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 0bda:0158 Realtek Semiconductor Corp.
Bus 003 Device 001: ID 0000:0000
Bus 007 Device 001: ID 0000:0000
Bus 005 Device 003: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 005 Device 002: ID 05da:30cf Microtek International, Inc. ScanMaker 4800
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Thanks in advance!

---

### Post by LewisTM on 2008-10-14
bump

---

