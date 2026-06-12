---
title: "Keyboard problems after 8.10 install"
date: 2008-11-19
forum: Hardware
---

### Post by eleifsp on 2008-11-19
Hey everybody. I've installed 8.10 after some problems with a previous install. However, the new install has some problems of it's own, particularly keyboard-related for myself. First, the arrow keys don't work (the up key takes a screenshot, while the others don't do anything at all).  Second, the space button by itself is opening gnome-do (I usually have to push super-space. To type this message, I have to hit shift-space at every word break). Finally, the multimedia buttons (which normally work out-of-the-box with Ubuntu) don't do anything at all.

I have an HP DV2000 entertainment-series notebook (specifically the 14.1 inch model with special-edition verve finish). If anyone else has one of these issues, I would love the help.

BTW, I have a separate partition for my Home folder, which may have had some custom key profiles in it. Would they have loaded themselves by default, and if so, how do I get my old one back.

Ow, hand hurting...



EDIT:

I fixed it.  It turns out that in my ~/.initrc file, it was loading my custom xmodmap.conf into xmodmap.  However, something in the kernel (or x, possibly) changed between 8.04 and 8.10, so the custom map had *wrong* written all over it.  Deleting that line and my custom map fixed everything.

---

