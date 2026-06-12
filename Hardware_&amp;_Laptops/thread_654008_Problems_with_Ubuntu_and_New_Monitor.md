---
title: "Problems with Ubuntu and New Monitor"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by Marfish on 2007-12-30
I recently bought a new monitor with a much higher resolution that seems to work fine when nrunning ubuntu. Unfortunately, Ubuntu doesnt seem to like the new resolution and wants have wiunodws fully blown up in only a corner using the old number of pixels. It also is a little odd when I use the cobe effect, as it looks fine except for the fact that everything out of the old resolution has an odd angled view of the cube. Is there any way to get it work on this resolution properly, its more of a mild annoyance than anything else. Help will be much appreciated.

---

### Post by taurus on 2007-12-30
Open a terminal and reconfigure your X server for the new monitor.

Applications -> Accessories -> Terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Now, restart X again with <Ctrl><Alt>Backspace.

---

### Post by Marfish on 2007-12-30
I tried out what you suggested, but it didnt seem to work. Im still having the same problems. I have weird lines going across certain areas of the screen, Non, inside the old resolution, but I still seems to be able to use the extra pixels, even if windows try to revert to the old resolution. Any others ideas about what this might be?

---

### Post by Marfish on 2007-12-30
I just realized that my laptop monitor was on at the same time as my new monitor. I think this is most likely the problem. How do I turn off my laptop monitor to let the new one run by itself?

---

### Post by Marfish on 2007-12-31
*Bump*

---

