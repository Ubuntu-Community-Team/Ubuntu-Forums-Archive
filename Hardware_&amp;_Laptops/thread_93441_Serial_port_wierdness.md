---
title: "Serial port wierdness"
date: 2005-11-22
forum: Hardware &amp; Laptops
---

### Post by briguy on 2005-11-22
Ok, I'm pretty sure I've got the correct serial port and correct settings.  I'm trying to connect to my ipaq with minicom, which is running Opie on Familiar Linux.  I've done this before without troubles on my old motherboard, with the new one I can't get it to connect.  My settings are correct at /dev/ttyS0 115200 8N1, no software / hardware flow control.  Here's the wierdness - when I dmesg I get: ```
Nov 21 23:08:24 localhost kernel: [4512727.475000] serial8250: too much work for irq4
```

Ideas anyone?  What I'm hoping for is a dpkg-reconfigure of the package that controls the serial port, I suspect this is the problem because of the new motherboard, but I don't know which package to reconfigure.  The problem could of course be any number of other things.

:confused:

---

### Post by briguy on 2005-11-23
Anybody....?

---

### Post by briguy on 2005-11-25
Okay, so I worked it out.  I was getting an error in dmesg serial8250: too much work for IRQ4.  Well, so I looked in my bios for my serial settings, and lo and behold serial A and serial B were both set to IRQ4.  I put them both to auto, and now everything works great.

---

