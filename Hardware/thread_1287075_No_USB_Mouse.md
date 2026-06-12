---
title: "No USB Mouse?"
date: 2009-10-09
forum: Hardware
---

### Post by reboskyz24 on 2009-10-09
Using Jaunty 9.04 on Acer Aspire 5000.  The USB ports recognize drives/flash memory, but I just plugged a USB mouse into the port (tried all three, actually) and the system doesn't recognize it.  I get no reading from the cursor and don't know how to check if an HID is plugged into a USB port using Linux.  Need a little help here.  Mouse is a Dynex USB optical mouse.

---

### Post by Yellow Pasque on 2009-10-09
First, make sure the USB ID's are up to date:
```
sudo update-usbids
```
Then, list USB devices.
```
lsusb
```

You'll probably want to look at the most recent system log messages after you plug the mouse in:
```
dmesg | tail -n 20
```

---

