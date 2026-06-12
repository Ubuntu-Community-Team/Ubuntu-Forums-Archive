---
title: "switching video card"
date: 2007-02-23
forum: Hardware &amp; Laptops
---

### Post by H3r3j3 on 2007-02-23
Greetings

I'm about to change my old Ati radeon 9200 for a new Nvidia Gforce 6200, I'm using Ubuntu 6.10, do I have to remove something or make any change to Xorg.cfg before removing the old video card? or I can do the switch without touching my linux config?

thanks

---

### Post by taurus on 2007-02-23
Maybe you need to edit /etc/X11/xorg.conf and replace the current Driver with **vesa**.  Then, shut it down and replace the ATI with the new nVidia card.  Reboot and see if X is up and running again.  Then, install nvidia driver for it.

```
gksudo gedit /etc/X11/xorg.conf
```

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by H3r3j3 on 2007-02-23
thanks!

---

