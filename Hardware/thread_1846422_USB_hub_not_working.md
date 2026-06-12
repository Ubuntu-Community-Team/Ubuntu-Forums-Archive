---
title: "USB hub not working"
date: 2011-09-19
forum: Hardware
---

### Post by uho on 2011-09-19
I have ubuntu 11.04 plugged into the built-in usb hub on my monitor HP ZR24w. Attached to the hub is a mouse and keyboard. 

Both receive power (led's are on) but ubuntu doesn't respond to them. How can I check to see whether or not ubuntu recognizes these devices?

---

### Post by Grenage on 2011-09-19
*lsusb* *should* return detected USB devices.  I've seen odd situations where USB hubs just didn't work correctly; I presume they work when connected directly to the PC - what about with only one device connected to the monitor?

---

