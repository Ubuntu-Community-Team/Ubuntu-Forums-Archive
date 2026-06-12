---
title: "HP Thin Client T5545 no LXDE on DVI but VGA works"
date: 2015-11-13
forum: Hardware
---

### Post by breitfuss on 2015-11-13
Hi,

I installed Lubuntu minimal installation on my HP T5545 Thin Client.
When VGA is connected it works just fine, when I connect DVI and boot up the screen stays black.
I can connect via SSH though and uploaded the Xorg.0.log just in case.

Any idea how I can get this to work with DVI?

Thank you.

---

### Post by blm-ubunet on 2015-11-13
Reading this suggests auto probing the DVI port does not work.
[http://linux.die.net/man/4/openchrome](http://linux.die.net/man/4/openchrome)

I would try the following..
Create (overwrite !) a /etc/X11/xorg.conf file:
```
xorg -configure
```

Add this driver option:
```
Option ActiveDevice "DFP"
```

---

### Post by breitfuss on 2015-11-16
Thanks for the tip, but unfortunately still unsuccessfull.
I'm thinking of just using vga...

---

