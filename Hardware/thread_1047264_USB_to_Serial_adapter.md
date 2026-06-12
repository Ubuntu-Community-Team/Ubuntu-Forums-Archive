---
title: "USB to Serial adapter"
date: 2009-01-22
forum: Hardware
---

### Post by jasonmichel on 2009-01-22
I have a USB to serial adapter that i am trying to use on Intrepid,  It is made by prolific.  How can i see if it is being recognized and what would it be listed as under DEV if i was to use a terminal emulator.  I can see it listed under usb devices on virtualbox, so i assume it sees it..Any help would be great

---

### Post by ModelM on 2009-01-22
It will probably show up as /dev/ttyUSB0, unless you have some other USB devices (cell phone, etc) plugged in. In that case the digit would change - /dev/ttyUSB1, /dev/ttyUSB2, etc.

---

### Post by jasonmichel on 2009-01-22
yep, i actually figured that out after extensive research, worked great with putty, Thanks for the reply

---

