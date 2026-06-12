---
title: "USB memorystick problem"
date: 2007-01-22
forum: Hardware &amp; Laptops
---

### Post by Bad_Byte on 2007-01-22
I'm wondering if there's a way to restart the USB system. Something that works like /etc/init.d/network restart but for USB. 

After a  reboot I can plug in a usb memorystick X (usualy less than 5) times before the machine refuses to see the stick as pluged in, same happens if I would use the safe dismount option.

A reboot fixes this, but I would rather avoid rebooting the machine that often.

---

### Post by skewray on 2007-01-23
maybe try:

rmmod usbcore
modprobe usbcore

Worth a shot, anyway.

---

