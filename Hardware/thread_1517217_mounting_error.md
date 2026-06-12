---
title: "mounting error"
date: 2010-06-24
forum: Hardware
---

### Post by gillisb91 on 2010-06-24
evrytime i boot up, i get the error:
error mounting /proc/bus/usb press S to skip mounting or Mfor manual recovery

Ant ideas as to what this means and how to fix it?

---

### Post by VH-BIL on 2010-06-24
A usb device is trying to mount on boot that is not available. Check out "/etc/fstab" to see what will try and mount on boot.

---

