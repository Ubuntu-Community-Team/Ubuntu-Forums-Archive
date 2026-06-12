---
title: "change resolution to larger than physical resolution"
date: 2010-03-16
forum: Hardware
---

### Post by josvanr on 2010-03-16
xrandr --output LVDS1 --mode 1280x800 --scale 2x2

This scales my screen size to 2400x1600 on my 1200x800 pixel
laptop screen, which is nice for some applications (eg gimp.)
It works well in gnome, but in kde, the last time I tried, 
it didn't work well. Messed up the desktop. Could anyone check
for me if it already works?

josvanr

---

### Post by maestrobwh1 on 2010-10-20
Did you ever find an answer to this?  This question is posted in many different forums but remains unanswered in all of the posts.  I must have seen almost 10.  

Anyone?  Bueler?  Anyone?

---

### Post by nnat on 2012-05-08
in my opinion, you can not change your pixel-dimension(or so called resolution) to larger than physical resolution. why? 

because physical resolution is the maximum value of pixels a display device can show. 

for example- if a 17 inch monitor has a physical(maximum) resolution of 1280x1024 pixels, it means it can display maximum of 1280 dots or pixels on each 1024 lines. 

now to show more it has to divide each pixel or dot, into less which is not possible because it is already the least unit on the screen and doing it will also affect things like horizontal & vertical Frequency and pixel clock.

---

