---
title: "HP PSC 1510 not detected"
date: 2006-08-26
forum: Hardware &amp; Laptops
---

### Post by bogler on 2006-08-26
I have an HP 1510 PSC, it is connected locally via usb.

When i try and set it up in Admin - Printing it teels me that there is no printer detected, i have had this printer working before - i simly plugged it in and rebooted. I have tried this and nothing - no detection?


hp-makeuri /dev/usblp0

 HP Linux Imaging and Printing System (ver. 0.9.7)
 Device URI Creation Utility ver. 2.5

 Copyright (c) 2003-5 Hewlett-Packard Development Company, LP
 This software comes with ABSOLUTELY NO WARRANTY.
 This is free software, and you are welcome to distribute it
 under certain conditions. See COPYING file for more details.

 Creating URIs for '/dev/usblp0':
 Trying bus: usb...
 Trying bus: par...
 [ERROR]: /dev/usblp0: Failed. Please check device node of device and try again.

I have created a symlink to /dev/usb/lp0 but still nothing.

Since i have updated Ubuntu my printer is borked

Can anyone please help?

---

### Post by bogler on 2006-08-26
please help, my system no longer sees my printer - it used to work fine - it must be update related, maybe usb related..

---

