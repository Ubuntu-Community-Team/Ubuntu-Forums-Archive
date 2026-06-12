---
title: "Cannot Switch to Low Resolution"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by bsalt on 2006-12-07
Hey guys! I noticed recently that I only have two available resolutions for my Dell Inspiron 6000 lcd screen. I only have 1280x800 and 1024x768 available to me, and when I switch to 1024, the screen is stretched. I would like to be able to switch to 640, 800, or even 1024 resolutions without stretching the screen as well.

How do I fix this?

---

### Post by dashnak on 2006-12-07
You could edit the "Screens" section in your xorg.conf
```
sudo nano /etc/X11/xorg.conf
```

---

