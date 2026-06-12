---
title: "Acer Aspire 9101WLMi, Radeon X600 blank screen"
date: 2005-08-04
forum: Hardware &amp; Laptops
---

### Post by moffen on 2005-08-04
I am the glad new owner of a "Acer Aspire 9101WLMi" laptop, but it is builted with a "Ati Radeon X600" graphic card.

It works okay with the default "ati" driver, but I have no hardware acceleration and that stuff.. I tried to install the "fglrx" driver, but when I reboot and start Gnome, it just show me a blank screen, without any fails.

What to do? I would like to get hardware acceleration on my new Laptop.

Any suggestions?

/Moffen

---

### Post by neowhale on 2005-08-05
I have a  Toshiba A80 laptop which come with X300 and has the same problem after installing fglrx driver. However after surfing for info, I came across a site [here](http://odin.prohosting.com/wedge01/gentoo-radeon-faq.html). Maybe you can try chage the "MonitorLayout" to "LVDS, AUTO". I haven't try it yet. I'll tell you if I get it.

---

### Post by jeremytaylor on 2005-08-05
Hi, 
I have an asus W3v with the x600. I had problems with the fglrx driver in the ubuntu repository but following the steps on [http://www.ubuntuforums.org/showthread.php?t=32495&highlight=ati+driver](http://www.ubuntuforums.org/showthread.php?t=32495&highlight=ati+driver)
I installed the newer driver from ATI with great sucess, really nice 3d graphics now.

I still haven't got the dual monitor setup working so if you do please let me know how!

Jeremy

---

### Post by moffen on 2005-08-05
[QUOTE=neowhale]I have a  Toshiba A80 laptop which come with X300 and has the same problem after installing fglrx driver. However after surfing for info, I came across a site [here](http://odin.prohosting.com/wedge01/gentoo-radeon-faq.html). Maybe you can try chage the "MonitorLayout" to "LVDS, AUTO". I haven't try it yet. I'll tell you if I get it.[/QUOTE]

Thanks, your tip worked for me. Now it starts up nicely :-)

---

### Post by neowhale on 2005-08-06
my X300 is also working fine now :D Now I'm playing TuxRacer.

---

### Post by moffen on 2005-08-06
[QUOTE=neowhale]my X300 is also working fine now :D Now I'm playing TuxRacer.[/QUOTE]

Hehe... me too.. I've also tested with TuxRacer :-)

---

