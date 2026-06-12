---
title: "screen resolution question"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by lacerado on 2006-11-27
I'm running 64-bit edgy w/ nvidia drivers.  My monitor (Proview PL926Wbi, 19" widescreen lcd) lists a max resolution of 1440x900, and this is what I'm running now.  Is there any way to increase the resolution, say, even if every pixel isn't represented?  I'm used to having more screen space than this on a similarly-sized monitor.  Everything is just too big.

---

### Post by geekworking on 2006-11-27
LCD resolution is fixed. On an LCD every pixel is a fixed physical element.  The size and number cannot be changed.  No matter what you set the video card to, there will always be 1440x900 dots on your screen. On a CRT, the size and number of pixels can be changed by varying the scanning speed.

You cannot discard screen pixels because the driver has no way to know what is important.  If you discard the first vertical row in a B it can become a 3 on the screen. How about discarding a decimal from a number.

The native resolution of the LCD will be the best possible display image that you can get.

---

### Post by drphilngood on 2006-11-27
I don´t know if this will be satisfactory but here´s what I did.  Go to:

**System -> Preferences -> Desktop Preferences/Gnome Control Center -> Font Preferences -> Details**

and decrease the **Resolution: dots per inch**.  This makes it seem that you have  ¨more screen space¨ by making everything smaller.

Hope this helps!

---

