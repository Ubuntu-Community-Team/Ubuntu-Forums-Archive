---
title: "nVidia; problem w quadro4"
date: 2007-07-03
forum: Hardware &amp; Laptops
---

### Post by eeyore76 on 2007-07-03
Hello!

Installed the nVidia restricted driver and the screen went black. Found the solution to this problem on this forum.
The driver seems to work, but not very well... the upper left portion of the screen shows the desktop alright, but a strip to the right is made up of multicolored lines, and the lower part of the screen is a copy op the upper part of the desktop.

Also, the panel is capable of 1600x1200, but I cant choose anything higer than 1400x1050...

I have seen people having this problem on other forums, but no solution to the problem... is there anyone here that has the same problem? Anyone who solved it?

Also, I am not quite sure exactly what version of Quadro4 this laptop has (Dell Precision M50)... How do I find out? Ubuntu identifies it as "NV17GL, quadro4 500 GoGl" and that might be true, but when I search the Internet most pages talk about quadro4 700GoGl in this laptop.

(I´m running Feisty right now, but I have had the same problem with other versions of Ubuntu.)

---

### Post by nostrilman on 2008-07-03
There is a very similar problem to this with Dell C840's, which are essentially the same laptop with different nVidia video cards.  It sounds like you're running the display panel that gives improper EDID information, I believe it was the Samsung 1600x1200, 15"

RxRitalin created a custom EDID, nvnew.raw.  Do a search for it and C840.  It may work for your laptop.

---

