---
title: "Moved PC and MX-320 printer, but now printer doesn't get jobs from PC"
date: 2022-06-29
forum: Hardware
---

### Post by cigtoxdoc on 2022-06-29
I have a Canon (now Lexmark) MX-320 printer/scanner.  Is is connected to a USB port.  I moved PC and printer from one room to another.  Now the printer will not print.  I know the USB connection is good because the scanner part works correctly.  Indeed, I used the same USB printer cable.  I also did an in-place upgrade from 21.10 to 22.04. Upgrade process was flawless and even kept Unity desktop.

When I got to printer properties, and do a print test page, the printer que icon appears momentarily in the top right-hand corner of the screen. The device URL is usb://Canon/MX320%20series?serial=2435E9&interface=1

Any ideas on how to fix this problem?

Thank you,

John

---

### Post by oldfred on 2022-06-29
Was it really using WiFi?

I would swear my Brother printer prints with USB, but has to have WiFi to scan when using 20.04. 
Have not fully tested since upgrading to 22.04 which supposedly has better printer drivers.

---

### Post by cigtoxdoc on 2022-11-14
Fixed.  Device URL is cnusbufr2:/dev/usb/lp1 . Make and model is Canon MX320 series - CUPS+Gutenprint v5.3.3

---

