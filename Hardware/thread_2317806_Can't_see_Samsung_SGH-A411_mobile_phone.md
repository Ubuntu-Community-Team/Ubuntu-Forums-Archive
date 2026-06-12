---
title: "Can't see Samsung SGH-A411 mobile phone"
date: 2016-03-20
forum: Hardware
---

### Post by oygle on 2016-03-20
Have a Samsung SGH-A411 connected via usb cable. It shows up here ..

> $ lsusb
Bus 003 Device 006: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 007: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 003 Device 004: ID 0c45:670b Microdia 
Bus 003 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 003 Device 013: ID 04e8:6601 Samsung Electronics Co., Ltd Mobile Phone
Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


but I can't see it under Dolphin.

---

### Post by ajgreeny on 2016-03-20
It might be worth looking at [http://ubuntuforums.org/showthread.php?t=2226702](http://ubuntuforums.org/showthread.php?t=2226702) which is a long thread now, having started some time ago, but it allowed me to connect to all android devices I have without any hiccups occurring along the way.

EDIT:
Having just done a quick search I see this is probably not a smartphone with android but an older style mobile phone, so unfortunately this may not help, but it could still be worth a try.

Do you know if the phone connects by default through MTP, or can you set it to connect as a mass storage device as well; if MSD is possible, change to that (the manual may give you a clue how) and see if you can then get to it in dolphin.

---

