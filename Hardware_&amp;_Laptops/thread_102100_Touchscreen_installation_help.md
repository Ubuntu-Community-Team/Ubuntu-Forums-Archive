---
title: "Touchscreen installation help"
date: 2005-12-11
forum: Hardware &amp; Laptops
---

### Post by spacifique1 on 2005-12-11
Hi.
I`ve got a touchscreen monitor and it connects through USB. I`ve got the software and everything on disk. The touchscreen is responding when touched but i need to install the software for calibration.
The monitor is a 3M M150. 

Anybody knows how to install the software for it.

---

### Post by idlewild on 2005-12-11
Calibration of touchscreen has been is largely a manual affair from what I've experienced but if you do have a calibration program then it will most likely be bundled with your X driver. The best driver for touch screens I've seen is [http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html](http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html)
which comes with a calibration program although I personally have never used it.

The alternative (which is what I did) is to watch the data stream from the panel and record the co-ordinates of the top left and bottom right of the screen. A program called evtest will format the data to be more readable.

---

### Post by schof on 2005-12-14
[QUOTE=idlewild]The alternative (which is what I did) is to watch the data stream from the panel and record the co-ordinates of the top left and bottom right of the screen. A program called evtest will format the data to be more readable.[/QUOTE]

I've got a similar problem (I'm trying to calibrate an EELY touchscreen <http://www.eelyecw.com/eelyeng/productline/ito.htm>.) Could you provide a little more detail about what you used to watch the data stream from the touchscreen and how you used that information?

Thanks very much!

---

