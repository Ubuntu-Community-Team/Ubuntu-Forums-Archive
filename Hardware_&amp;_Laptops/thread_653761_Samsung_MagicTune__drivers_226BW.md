---
title: "Samsung MagicTune / drivers 226BW"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by dethredic on 2007-12-30
I just got a 226BW, I have no problems with the resolution, but I do not like the colours.

I just pluged it in, and it worked, but I was wondering if Samsung had linux drivers or a linux version of magictune.

If they don't, are there 3rd party alternatives?

---

### Post by taurus on 2007-12-30
What graphic card do you have and I assume you have installed a driver for it?  What happens if you reconfigure X server again since it's a new monitor and your X server is configured for the old one.

Applications -> Accessories -> Terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
You can restart X with <Ctrl><Alt>Backspace or reboot if you wish.

---

### Post by dethredic on 2007-12-30
Ok, I did that.

I have a Nvidia 8800GTS video card. Yes I have the drivers for it.

---

### Post by dethredic on 2007-12-31
So, is there anything I can do?

---

### Post by maduranga on 2008-01-01
me too have 226BW. I got the same problem.

---

