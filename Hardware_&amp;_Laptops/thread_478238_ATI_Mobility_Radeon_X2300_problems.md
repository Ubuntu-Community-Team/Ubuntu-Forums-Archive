---
title: "ATI Mobility Radeon X2300 problems"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by ShagzModo on 2007-06-19
Hi All!

I have this sweet laptop that has a ATI Mobility Radeon X2300 VGA card build in.
I can get it to work. Ubuntu is giving me only 1024x768, this should be 1280x800
Already tried installing the standard ATI Accelerated display driver, wich completely crashes the system.

Any suggetions or solutions?

---

### Post by ShagzModo on 2007-07-15
I solved my problem bye installing the standard restricted proprieatry driver.

---

### Post by ckh on 2007-07-21
I had excact the same problem when I just changed my laptop to HP 6910p
but I just solved this probelem.

steps below:

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo /etc/init.d/gdm restart

(This solution was form [http://terenzioberni.blogspot.com/2007/06/ubuntu-704-on-asus-z53jr-f3jr.html](http://terenzioberni.blogspot.com/2007/06/ubuntu-704-on-asus-z53jr-f3jr.html))


-ckh

---

### Post by maclenin on 2007-08-19
**ckh:**

Thanks for posting this solution - it worked for my Ati Radeon x2300/HP 6910p, as well!

The only difference in my procedure was to...

```
sudo shutdown -r +0
```

...vs.

sudo /etc/init.d/gdm restart

---

### Post by dgrafix on 2007-10-09
Great, this worked very well to get me back into graphics :)

Now to fix the 3D :/

Im getting :
Xlib: extension "XFree86-DRI" missing on display ":0.0"
Direct rendering: no
OpenGl render string: Mesa GLX indirect

---

