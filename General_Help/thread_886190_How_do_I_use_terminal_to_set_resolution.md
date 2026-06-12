---
title: "How do I use terminal to set resolution?"
date: 2008-08-10
forum: General Help
---

### Post by s3a on 2008-08-10
I had 1680x1050 res working fine until I undusted my video card with a wet q-tip. Now I only get 1280x800! I did sudo dpkg-reconfigure xserver-xorg and it only lets me reconfigure my keyboard settings and not my display settings! Please help!

---

### Post by michael1234 on 2008-08-10
```
xrandr --fb [width]x[height]
```

where [width] and [height] are the dimensions in pixels.

---

### Post by michael1234 on 2008-08-29
Also try xrandr -s <width>x<height>

You may have more luck this way if --fb won't cooperate.

---

### Post by werries on 2008-08-29
...you got your graphics card wet?

---

