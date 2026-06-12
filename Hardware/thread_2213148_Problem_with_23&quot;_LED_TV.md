---
title: "Problem with 23&quot; LED TV"
date: 2014-03-25
forum: Hardware
---

### Post by yuri3 on 2014-03-25
I have a dual boot windows 7 and xubuntu 13.10 on my lenovo x200  laptop. When i connect to my 23" toshiba LED tv on windows 7 thru vga  connector (no HDMI port), it can work correctly on 1360x768 resolution.  But on xubuntu, i can only get 1024x768. So i browse some forums,  and got this:

cvt 1360 768
xrandr --newmode "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 1360x768_60.00
xrandr --output VGA1 --mode 1360x768_60.00

It's  working but not as expected, the 1360x768 resolution does not fill the  entire screen, leaving 2" blank on left and right of the screen (as i  said, it is working fine on windows 7, it filled all the screen with the  same resolution).
I took out my other asus laptop ux31 with standard  installation of linuxmint 16 xfce, connect to the same tv thru HDMI,  its working perfectly. FYI: both laptops are using intel graphics.

How do i solve this. Ty.

---

### Post by yuri3 on 2014-03-27
Okay, I solved the problem by deleting xubuntu.

---

