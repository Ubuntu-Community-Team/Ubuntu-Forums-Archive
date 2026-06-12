---
title: "Yoga 2 Pro laptop pixel layout"
date: 2014-05-14
forum: Hardware
---

### Post by jamapii on 2014-05-14
Hi,

I have seen that the 3200x1800 pixel grid is unusual. Other laptops have a simple rectangular grid. The yoga 2 pro looks more like a chess board, the black spot between the pixels alternate between consecutive lines. I couldn't find any information anywhere about the layout.

Is the resolution not really 3200x1800, but only half, by leaving out every other pixel? Or is just the rgb order alternating?

This is extremely visible with red on black in an xterm on Ubuntu 14. The characters are very blurry. This is with the default size in pixels, I have not tried to resize anything to make it easy to read for others.

Btw, does the Ubuntu 14 default installation (I booted a USB) have options for subpixel font rendering? Windows seems to have, but does not tell what it is, it only shows examples of text to choose. Other flavors of Linux did have that kind of options before, but that was older versions of Gnome and such.

I guess it would be hard to get a font rendering for alternating rgb order. Whenever an xterm is moved for an odd number of pixels, it has to be re-rendered, or at least applied to new text.

---

### Post by jamapii on 2014-05-16
I found some information. It's a PenTile RGBW. This means that only half the pixels are RGB, and the rest are W, that means monochrome.

The pixels are mixed nicely like a chess board, so the real effective visible resolution is more like 3200/sqrt(2)x1800/sqrt(2) RGB + 3200/sqrt(2)x1800/sqrt(2) monochrome pixels.

Normal (small) text will be slightly blurry if it's colored. High-contrast or black/white text will be ok to read.


edit: fix effective resolution

---

