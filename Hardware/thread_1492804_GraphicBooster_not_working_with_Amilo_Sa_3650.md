---
title: "GraphicBooster not working with Amilo Sa 3650"
date: 2010-05-25
forum: Hardware
---

### Post by Houchy on 2010-05-25
Hello,

I have a Fujitsu Amilo Sa 3650 with Ubuntu 10.4 installed. This laptop comes with an external graphics card (ATI HD 3870) call the [GraphicBooster]("http://ts.fujitsu.com/home/products/notebooks/amilo_graphic_booster.html").

I installed the ATI proprietary driver directly from Ubuntu, the laptop Graphics card (ATI HD 3200) works perfectly. However, the external graphics card is not recognized even though it is supposed to be supported by ATI driver.

Does anybody have a recommandation?

Thank you for your help.

---

### Post by Mikethk on 2010-07-19
I can actually help with this....


The driver is specific for the booster.... You need a specific driver aint represented for Linux.... You will never make it work is my guees. 

They dont even update the driver which is sad for us with this else perfect solution.

---

### Post by wayne__ on 2010-09-17
Hi there, 

if you create another xorg.conf with the GraphicsBooster as specified output-device (you can get the ID with lspci) it should work...gave me 20000 instead of 5000 frames in glxgears (with radeonhd drivers). 
you have to switch xorg´s  if you want to run on the internal graphics, and the laptop will show the ubuntu-splashscreen if you´re on external monitor.


btw: got any ideas about how to fix those darn standby-issues?

---

