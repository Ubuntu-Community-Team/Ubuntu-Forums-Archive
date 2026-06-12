---
title: "sis m760gx video driver"
date: 2008-08-07
forum: Hardware
---

### Post by txbbq on 2008-08-07
Help, I am a noobee!  Just loaded Heron and am having trouble with my video card.  It is a laptop.  Acer Aspire 5000 with an SIS M760GX video card.  I seem to need a propriatery driver.  Any ideas on what I need and where to get it?

Thanks so much
M

---

### Post by phidia on 2008-08-07
Open a terminal from Apllications > Acessories > Terminal and enter this: > sudo dpkg-reconfigure -phigh xserver-xorg

The program that opens will ask questions about your video card and screen.

Select 'sis' for your video driver and after you save your settings restart the xserver by doing Ctrl+Alt+backspace.

---

### Post by txbbq on 2008-08-08
Tried this and the program that runs only asks about my keyboard.  Never about video driver.  Any suggestions?

Thanks

---

