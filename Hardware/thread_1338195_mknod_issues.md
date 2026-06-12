---
title: "mknod issues"
date: 2009-11-26
forum: Hardware
---

### Post by rafaelsousa on 2009-11-26
I'm using karmic koala, and I'm trying to perform a mknod to create a USB device.
It executes the command without problems, but it's not creating the /proc/devices entries. Is there something different in the way karmic is performing mknod? My commands were:

#mknod /dev/ttyUSB0 c 188 0
#mknod /dev/ttyUSB1 c 188 1
#mknod /dev/ttyUSB2 c 188 2
#mknod /dev/ttyUSB3 c 188 3

But 
#cat /proc/devices | grep ttyUSB

returns nothing.

---

