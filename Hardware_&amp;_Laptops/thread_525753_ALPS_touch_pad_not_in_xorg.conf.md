---
title: "ALPS touch pad not in xorg.conf"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by emarkman on 2007-08-14
Hi,
I have installed 7.04 on an old Zepto laptop with an ALPs touch pad. The touch pad works but is extremely sensitive and I get a "click" when I touch it. Very annoying.....
Problem is that it does not show up in xorg.conf. I have the keyboard and a "configurated mouse" and then 3 Wacom devices. That is all. Is there a way to have Ubuntu search for it again?
All help is appreciated.
Thanks

---

### Post by ugm6hr on 2007-08-15
Just add the appropriate sections to xorg.conf manually.  Have a look at some of the examples given in my signature link (post your xorg.conf).

You will find that GSynaptics will then work, and you can manually edit other options in xorg.conf (see the link to how-to on touchpads from that first page).

---

