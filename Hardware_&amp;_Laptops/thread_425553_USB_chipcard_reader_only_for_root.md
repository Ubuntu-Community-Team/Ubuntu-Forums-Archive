---
title: "USB chipcard reader only for root"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by FunFubar on 2007-04-27
Hi guys,

I have a problem with my "Reiner SCT Cyberjack" USB chipcard reader. My homebanking application does not detect the reader and while trying to track down the problem I discovered that the device is not listed when I call "lsusb":
[INDENT]Bus 002 Device 003: ID 046d:c01d Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 04a9:10a5 Canon, Inc. 
Bus 001 Device 001: ID 0000:0000  [/INDENT]

But a call to "sudo lsusb" shows the device:

[INDENT]Bus 002 Device 003: ID 046d:c01d Logitech, Inc. 
Bus 002 Device 002: ID 0c4b:0300 Reiner SCT Kartensysteme GmbH cyberJack pinpad(a)
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 04a9:10a5 Canon, Inc. 
Bus 001 Device 001: ID 0000:0000  [/INDENT]

Now I wonder why that happens. As you can see all other USB devices are listed. How can I give all users access to the reader and not only su/root? It'd be great if anyone could give me a hint on where to look or what to do.

Regards
Fubar

---

### Post by FunFubar on 2007-04-29
If anyone else has the same problem, this is the solution:

sudo chmod 666 /dev/bus/usb/004/004 

Regards,
Fubar

---

