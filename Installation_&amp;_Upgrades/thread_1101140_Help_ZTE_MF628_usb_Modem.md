---
title: "Help ZTE MF628 usb Modem"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by Gayangm on 2009-03-20
I cant install or configure  my ZTE MF628 usb modem....
Can anyone help me to get use of it in ubuntu... PLzz

---

### Post by GeorgeVita on 2009-03-20
Hi **Gayangm**, what version of Ubuntu are you using?

after boot, plug your modem to the USB port, wait 15 seconds,  open a terminal window and: **lsusb**
if this command lists something like: **Bus 001 Device 002: ID 19d2:0015**
then Ubuntu 8.10 may work directly.

If the lsusb gives 19d2:2000 follow instructions from **post #8** [http://ubuntuforums.org/showthread.php?t=1065934](http://ubuntuforums.org/showthread.php?t=1065934)

Regards,
George

---

