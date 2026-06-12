---
title: "Touchpad Scrolling Area"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by supersatellite on 2007-08-07
The Synaptics touchpad on my Gateway NX570X has an area on the right for vertical scrolling, separated from the rest of the touchpad by a small ridge. However, Feisty extends this scrolling area onto the main part of the touchpad, so I tend to scroll accidentally. Is there any way to edit this behavior? I tried qsynaptic but that didn't work.

---

### Post by ugm6hr on 2007-08-07
You need to edit xorg.conf.  This will tell you about all the settings you need to add for the Touchpad:

```
man synaptics
```

If you need help finding out the coordinates for the borders - you can use:
```
synclient -m 500
```

This will list the *x* and *y* coordinates (along with other details e.g. pressure etc) of any place you touch.  So if you run it, and then place your finger on the scroll area, it will tell you what the coordinate is, so you can set that as the value in Option "RightEdge" "*x*" in xorg.conf

---

### Post by supersatellite on 2007-08-07
Awesome!! Works beautifully. Thanks for the info

---

