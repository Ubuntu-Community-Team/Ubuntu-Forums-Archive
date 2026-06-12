---
title: "startup error message, graphics card related?"
date: 2006-04-08
forum: Hardware &amp; Laptops
---

### Post by xxFelixDCatxx on 2006-04-08
Okay so I've installed and everything and as I go to boot my laptop up, it now reads that there's a problem with the 'xserver'. I'm relatively new to linux, but after reading into the error message details a bit, I believe this is a graphics application.

Does anyone know what I'm talking about/have any advice?

-linux n00b

---

### Post by taurus on 2006-04-08
Maybe you just need to reconfigure X for your video card and by the way, which one do you have?  I assume you are at a terminal since X doesn't work.  Then type
```

sudo dpkg-reconfigure xserver-xorg

```
And to play it safe, pick "vesa" as the driver for your video card...

---

