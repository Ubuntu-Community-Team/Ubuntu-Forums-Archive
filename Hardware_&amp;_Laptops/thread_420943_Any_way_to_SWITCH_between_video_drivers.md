---
title: "Any way to SWITCH between video drivers??"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by superyounan1 on 2007-04-24
The age old story -> I have an ATI.

Drivers that come with ubuntu = enable desktop effects
Drivers made by ATI = no desktop effect, everything else is better though

Is there a way to somehow have both drivers installed, and to be able to switch simply between the two, like run a script, have it do its thing, then restart the computer or log off and back on, and be using the other driver? Enlighten me

---

### Post by superyounan1 on 2007-04-24
bump

---

### Post by jpeddicord on 2007-04-25
From the terminal:
```
sudo dpkg-reconfigure xserver-xorg
```
Pick a video driver from that list. (Original Ubuntu-shipped one is Vesa.)
You will have to go through the rest of the steps to complete the setup also. Once you are done, press *Ctrl+Alt+Backspace* to restart X.

Jacob

---

### Post by superyounan1 on 2007-04-26
> **jacobmp92 said:**
> From the terminal:
```
sudo dpkg-reconfigure xserver-xorg
```
Pick a video driver from that list. (Original Ubuntu-shipped one is Vesa.)
You will have to go through the rest of the steps to complete the setup also. Once you are done, press *Ctrl+Alt+Backspace* to restart X.

Jacob

Thanks a lot jacob!

---

