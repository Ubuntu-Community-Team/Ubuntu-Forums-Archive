---
title: "xorg.conf needed /for ASUS A6R(?)/"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by tzg6sa on 2008-01-15
Hi!

My screen don't want to go in the normal 1280x800 resolution, after I tried to connect an externel display to my machine. Ubuntu don't recognise any more my display and my video card. I thing the problem is somewhere in the xorg.conf, but I haven't got a saved old version of xorg.conf.

Could you tell me, how could I set the correct resolution? I have tried a lots of things, but noone has helped.

If you have a notebook display with a resolution 1280x800 and an ATI Radeon X200 video card, please send your xorg.conf file to me! I would be very greatful!

Cheers,
Zoli

mail: [email]tzg6sa@gmail.com[/email]

---

### Post by tzg6sa on 2008-01-15
I have found the solution:
sudo dpkg-reconfigure -phigh xserver-xorg

Now it works.

---

