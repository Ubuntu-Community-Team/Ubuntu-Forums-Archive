---
title: "integrated modem issue, gutsy on acer aspire 5920G (also other santa rosa i guess)"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by Netrunner on 2007-11-03
All work fine... except the integrated modem.
Opening network manager i can set parameters but nothing happen.
Using gnome ppp is the same, no modem: analogic usb or isdn (i tried before the analogic then the others)

i tried console to understand something
cat /dev/modem
no directory found (why not i/o error?)
cat /dev/ttyS0
i/o error
cat /dev/ttyS1
i/o error
cat /dev/ttyS2
i/o error
cat /dev/ttyS3
i/o error

Of course i didn't. =)
All i know is that i'm missing something... but don't know what.
Nobody got it work?
Maybe it's something with the kernel (wich at the moment is 2.6.22-14-generic)? 
Hope someone help me find a solution.

---

### Post by Netrunner on 2007-12-07
[http://www.nabble.com/Aspire-5920g,--Turkey,-kernel-2.6.22-12-generic-t4577939.html](http://www.nabble.com/Aspire-5920g,--Turkey,-kernel-2.6.22-12-generic-t4577939.html)
[http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
[http://linmodems.technion.ac.il/archive-seventh/msg02442.html](http://linmodems.technion.ac.il/archive-seventh/msg02442.html)

a possible solution i guess

 i still  haven't made tests

---

