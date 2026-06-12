---
title: "deactivating touchpad"
date: 2006-10-02
forum: Hardware &amp; Laptops
---

### Post by goneskiing on 2006-10-02
is it possible to deactivate the touchpad when a mouse is plugged in - or make the touchpad way less sensitive ?   problem is as I type my hands cross the touchpad and the cursor jumps all over the place.

---

### Post by billyfoxtrot on 2006-10-02
I'm not sure about deactivating it when the mouse is plugged in, but what I did to fix this problem was turn of the touchpad tap.  That way I don't have to worry about bumping the touchpad and having the cursor move.

To do this, you add this line to your /etc/X11/xorg.conf file, under the Synaptics touchpad part:

```
Option   "TouchpadOff"   "2"
```

This doesn't turn your touchpad off completely, only tapping.

---

### Post by gigiya on 2006-10-02
When I ran Windows, I had set my touchpad to be disabled when a mouse was plugged in through the BIOS.  That didn't work in Linux, so I had to disable it completely in BIOS.

---

