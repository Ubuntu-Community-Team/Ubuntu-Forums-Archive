---
title: "Epson Aculaser CX16 color prints"
date: 2012-12-14
forum: Hardware
---

### Post by Finlandia on 2012-12-14
Hi,

I have:

- Ubuntu 12.10
- Epson AcuLaser CX16 printer
- KONICA MINOLTA magicolor 1600W Foomatic/foo2lava (recommended) driver.

And when I print:

- if I print a printer test page, it will be with full color.
- if I print any other page, it will be monochrome.

Anyhow: if I will start, for example, the LibreOffice and from there I will open the File Menu -> Print -> Properties -> Device tab -> Color Mode, the selected value is "Color - use ICM color profile". And in the same place I'm selected also ICM Color Profile: "km-16* (default)".

In the tab, the other selections with drop-down menus, are:

Printer Language: PDF
Color: from the driver
Color Depth: 24 Bit

(I'm not sure whether this terminology in English or not. I'm using the Ubuntu in Finnish.)

BUT: these same settings are is the printer settings when I print the test page.

What's wrong?

Thanks!


-Finlandia

---

### Post by Finlandia on 2013-02-23
No ideas?

---

### Post by pdc on 2013-02-24
> KONICA MINOLTA magicolor 1600W Foomatic/foo2lava [COLOR="Blue"](recommended)[/COLOR] driver.

I am unclear where you got the printer driver from that you are using;

from OpenPrinting, they only have reference to the AL-CX21 

[http://www.openprinting.org/printer/Epson/Epson-AL-CX21](http://www.openprinting.org/printer/Epson/Epson-AL-CX21)

and it works perfectly with the Postscript-Epson

........I note the AL-CX21 is also a colour printer..........

........Epson also supply linux printer drivers

[http://download.ebz.epson.net/man/linux/laser.html](http://download.ebz.epson.net/man/linux/laser.html)

.......you may care to work through this latter page;

.........if it is helpful to you, your feedback would help many other users

---

### Post by Finlandia on 2013-03-06
> **pdc said:**
> I am unclear where you got the printer driver from that you are using;

The driver came with Ubuntu. I didn't load it separately.

> **pdc said:**
> from OpenPrinting, they only have reference to the AL-CX21 
and it works perfectly with the Postscript-Epson

I tried it earlier (and again today) but I can't install it. During installation it will ask amount of the memory and tray options but the Continue/Done/Finish button ("Toteuta" in Finnish) is gray and I can't click it.

> **pdc said:**
> ........Epson also supply linux printer drivers
[http://download.ebz.epson.net/man/linux/laser.html](http://download.ebz.epson.net/man/linux/laser.html)

I tried this too but the results was same: the Finish button is not clickable during installation process. Only Cancel works.

BUT! Now I tried Ubuntu's default driver: "KONICA MINOLTA magicolor 2530 DL Foomatic/foo2lava" ... and now it works! It will print colors and all other great! (Except if I will change the resolution to 2400x1200... :) )

Anyhow, thanks for the answer! ... In principle it was not the correct answer but it motivated me to search a new driver.


Finlandia.

---

### Post by pdc on 2013-03-06
well done........delighted it has all worked out for you.......enjoy! 

others will find your post very helpful; best wishes

---

