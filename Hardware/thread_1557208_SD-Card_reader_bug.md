---
title: "SD-Card reader bug"
date: 2010-08-20
forum: Hardware
---

### Post by Daniel0108 on 2010-08-20
Hi!
If I insert a SD card into my internal SD-Card-Reader, Ubuntu 10.04 doesn't show me the SD-Card.
Only if I reboot my Laptop with inserted SD-Card, Ubuntu shows the SD-Card.
Is that a bug?
If it's a bug, I hope it will be fixed soon. Because it's a bit annoying.
Yours,
Daniel

---

### Post by efflandt on 2010-08-20
Look at the tail end of **dmesg** after inserting SD card.  Multi-card readers in desktops are often USB, but built-in card readers in laptops are usually some other block device (not an sd device and not usb mass-storage).  If it is not usb, you probably cannot boot from it, and might have to mount it manually.  I generally use a usb reader instead, since my built in my 2006 laptop SD reader cannot read faster SD or SDHC, but even an old Lexar usb reader can.

---

### Post by Daniel0108 on 2010-08-20
Oh, okay, thanks :P
I thought it was a bug ;)
Then it's okay...
Yours,
Daniel

---

