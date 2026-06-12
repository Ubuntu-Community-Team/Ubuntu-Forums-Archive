---
title: "Canon PIXMA MP190 Scanning Requires Root"
date: 2009-08-17
forum: Hardware
---

### Post by coldReactive on 2009-08-17
I started doing this, because my scanner requires root access after make/install the latest CVS Snapshot of sane-backends...

> **Patient0 said:**
> Ok, so not one to be beat, I have done a little bit of snooping. I have found out that the scanner is always on the 005 bus, only the device number changes. So after learning a few more commands I run the folloowing straight after rebooting:

#sudo chgrp -hR scanner /dev/bus/usb/005


This worked so onto finding an automated way of delivering this line, remembering it needs root access. My solution was to do this:

- Open terminal
- sudo -s -H
- scanimage -L
- record the two numbers after libusb, the first is the bus number
- cp /etc/rc.local /etc/rc.local.bak
- gedit /etc/rc.local
- before: exit 0 - type: chgrp -hR scanner /dev/bus/usb/005 (insert your bus number instead of 005)
- close and save
- reboot

Remembering that if xsane errors when closing then it is due to saving preferences issues, just go in preferences and untick save preferences.

If this is bad practice then please tell me. But it has seemed to resolve the problems.

That to all who have helped -- Linux Rules!

But what if scanimage -L gives the following message and no libusb?

```
device `pixma:04A91734_514865' is a CANON Canon PIXMA MP190 multi-function peripheral

```

---

### Post by coldReactive on 2009-08-18
Bump

---

### Post by coldReactive on 2009-08-19
Bump

---

### Post by coldReactive on 2009-08-21
Bump

---

### Post by coldReactive on 2009-09-10
Bump again

---

