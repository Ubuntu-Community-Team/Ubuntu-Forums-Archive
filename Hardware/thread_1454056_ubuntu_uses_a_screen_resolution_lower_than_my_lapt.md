---
title: "ubuntu uses a screen resolution lower than my laptop can support"
date: 2010-04-14
forum: Hardware
---

### Post by yinglcs2 on 2010-04-14
Hi,

I have installed ubuntu 9.10 on my laptop.
In System->Display, the best resolution I allow me to use is 1280x700. But my laptop can support 1600x900.

So how can i change it?
I tried 
 xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
and add that in /etc/gdm/Init/Default

But that does not help.

---

