---
title: "Turn off LCD when external monitor attached"
date: 2007-09-16
forum: Hardware &amp; Laptops
---

### Post by Linicks on 2007-09-16
After I attach an external monitor (via VGA port), I can get it to work great - but the laptop lcd stays on.  If I close the lid, then both the laptop lcd _and_ the monitor turn off :)

I have tried:

Ctrl + Alt + F1, then use the laptop screen change keys fn F8 to turn off lcd and turn on monitor (works fine).  Then I sudo /etc/init.d/gdm stop, then sudo /etc/init.d/gdm start and X starts again fine - but on BOTH displays again!

Llaptop fn F8 keys do not work directly in X for some reason.

I am beat how to do this - any help welcomed please.

Nick

---

### Post by chuckao on 2008-01-21
I have the same problem!! I'm using a Dell Inspiron 6400 (E1505) with ATI x1300 video device.

cheers

---

