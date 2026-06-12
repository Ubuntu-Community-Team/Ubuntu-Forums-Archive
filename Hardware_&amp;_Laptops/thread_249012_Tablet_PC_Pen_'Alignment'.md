---
title: "Tablet PC Pen 'Alignment'"
date: 2006-09-01
forum: Hardware &amp; Laptops
---

### Post by mapage on 2006-09-01
I'm sure I've see how to do this here, but I can't find the post...  

The mouse pointer doesn't match with where the stylus is touching the screen when the screen has been rotated using xrandr and xsetwacom so that both the stylus (and cursor and erasor) rotate with the screen.  (It would be nice if grandr and xrandr did this for you.)

The orientation appears to be correct.  If you move the stylus 'up' then the mouse pointer moves up and so on.  But it appears as though the screen is the wrong shape.  There is one corner where the two will match up, but as soon as you move away, the geometry doesn't match anymore.

Anyway, I don't think I'm explaining myself well, so I will just put this out there.

Thanks for any help.

---

### Post by 23meg on 2006-09-08
I think you'll need to adjust the Bottom/Top X/Y parameters with xsetwacom. See [this]("http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom").

---

