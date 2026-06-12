---
title: "any &quot;how to&quot;to use lower graphic modes ?"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by willemijns on 2007-10-19
hi,

what is the lowest graphic mode when our graphic card is not recognized ? what modes we can
try in waiting for a new release of ubuntu 7.10 ?

vga / vesa/ svga... ? 

someone can post a method and stick it ?

---

### Post by nawitus on 2007-10-19
If X fails, try selecting the vesa driver and select a resolution you like (1024x768 should be enough), then start up gnome and try to configure your graphics card from there.
```

sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start

```

There are actually many guides for these kinds of problems, just search around.

---

