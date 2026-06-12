---
title: "ATI Radeon X1100 and compiz-xgl"
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by nguyenx86 on 2007-12-10
I've installed XGL server and Compiz Fusion smoothly, but the problem is that I can't used Google Earth anymore and MPlayer displayed creepy as well (alway stretch out of the screen). Games as well. When I played 3D games (like Chrominum,Super Tux Card), they wouldn't stretch to the screen or change the screen's resolution and still be a small windows in a black screen.
Thanks for any help !

---

### Post by erfahren on 2007-12-10
googleearth doesn't run well (if at all) under xgl. The other problems probably are xgl related. There's really not much to be done except run those apps with XGL (and desktop effects) disabled or *try* updating to the new version of the ATI (fglrx) driver that doesn't require it. (I've personally never had much luck with that).

if you're using Gutsy you can disable XGL by creating the file: ~/.config/xserver-xgl/disable

you can just do:
```

touch ~/.config/xserver-xgl/disable

```
and delete it to re-enable it.

I actually created a little script to enable/disable with a launcher when I was using Gutsy (I reverted back to Feisty because of the suspend problems).

---

### Post by nguyenx86 on 2007-12-11
Uhm, I had done it before (a small tooltiptext had appeared after I installed XGL noticed me about that)
Anyway, thanks so much.
ATI's card is truly not suitable for Linux.:(

---

