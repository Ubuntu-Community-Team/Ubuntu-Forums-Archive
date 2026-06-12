---
title: "Intel GMA 945 , compiz, duael head"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by wireless on 2007-10-26
hey all
is there a way to have desktop effects with  Intel GMA 945 and Virtual larger than 2048x2048 ?
(dual-head)

thnx !
:):guitar:

---

### Post by straylight on 2007-10-26
I'm sorta in the same boat as you.  I have a Lenovo T60 with an internal 945 -- Mirroring works just fine with compiz but if i try to make my external Dell LCD the primary and extend onto the 14 inch laptop display i get problems.  I kind of have the dual display extension onto the laptop working but i lose compiz and the laptop display is set to 800x600 so if you drag a window from the external to the LCD the app wont fit on the screen.

If anyone has suggestions/solutions they would be greatly appreciated! :)

---

### Post by MaximusTG on 2007-10-26
No, that's not possible, has to do with maximum texture size, above 2048x2048, DRI gets disabled.

However, check this page:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.06.1_on_a_ThinkPad_R60e#Ubuntu_7.10_with_Intel_Graphics_Media_Accelerator_950](http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.06.1_on_a_ThinkPad_R60e#Ubuntu_7.10_with_Intel_Graphics_Media_Accelerator_950)

It deals with xrandr, and has some stuff about moving the "area" occupied by the screens around in the virtual screen. I don't know however, if it is possible to put (for example, if you have 2 1280x1024 screens) the first screen at the top of the 2048 x2048 square, and the second one below that, starting at 1025 vertical, AND putting at right or left of one another. That's up to you to experiment with..

---

### Post by wireless on 2007-10-26
I'll check it out and post the results if any..
thnx mate

Edit:
I already read this article. Its very informational and helped me to understand how the all thing ticks but offers no solution to the issue. aperently i must have Virtual size at 2048X2048 or more to be able to use dual head. 
so i rather have dual than 3d :)

---

### Post by Xvani on 2007-11-13
If you (vrtually) place the screens on top of each other, the two screens can have 2048 in vertical resolution.

That is 1024 on two screens (vertical)

Enough for me.... :)


For example, I have a 1680x1200 LCD and a 1280x800 laptop display :)

---

