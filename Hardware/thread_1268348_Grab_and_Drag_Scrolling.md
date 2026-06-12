---
title: "Grab and Drag Scrolling?"
date: 2009-09-16
forum: Hardware
---

### Post by victorhooi on 2009-09-16
heya,

I was wondering if there's a generic way to get grab-and-drag scrolling (as used in many PDF readers, like Acrobat, Okular etc.)

There's a Firefox extension called Grab and Drag, which does it in Firefox:

[http://grabanddrag.mozdev.org/index.html](http://grabanddrag.mozdev.org/index.html)

and for Windows, there's a program called MouseImp ([http://www.mouseimp.com/]("http://www.mouseimp.com/")), which does it generically.

However, I'm wondering if there's an equivalent for Linux that also does it generically?

I'm using a Lenovo X200 Tablet, which has a touch-screen, hence it's actually quite useful on this machine (or on any tablet PC really, even one without touch). With the Firefox extension, the grab-and-drag scrolling is turned on for all mouse inputs at once (mouse, tablet stylus, touch etc.). I'm wondering if it's possible to distinguish between the different mouse devices under Xorg, and switch it on for only one?

Cheers,
Victor

---

### Post by YSN on 2010-10-19
I had been looking for a MouseImp alternative a long time as well an just found it. It is not exactly what you wanted: it inverts your movement by default, like the corresponding setting in MouseImp did, but this works even better IMHO, e.g. on large pages.

Just try Gpointing from the Ubuntu Software-Center

or

```
sudo apt-get install gpointing-device-settings
```


You need to start the tool, activate mouse-wheel-emulation and choose your desired mouse button (right button is number 3 in my case).

Best
YSN

---

