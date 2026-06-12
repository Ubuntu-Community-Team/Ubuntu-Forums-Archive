---
title: "Ubuntu drivers available for Mobility Radeon X1400"
date: 2017-09-02
forum: Hardware
---

### Post by jack6128 on 2017-09-02
Graphics in About This Computer is listed as "Gallium 0.4 on ATI RV515". I am having trouble getting Google Earth to display correctly. I  tried upgrading to Ubuntu 17.04 but that didn't work. Previously on 16.04 I made sure I had the necessary files (I come from Windows) installed according to several different webpages on the subject of installing GE on Ubuntu. A different graphics driver seems to my last hope. The computer is a Lenovo ThinkPad T60 with an Intel Core2 Duo T7200 CPU @ 2.00GHz and 3GB of RAM. Are there any alternative graphics drivers I can try?

Thanks,
Jack

---

### Post by QIII on 2017-09-02
No.  Unfortunately there is no other Linux driver.  Proprietary support for that card ended in 2009.  There is only the open source driver that is installed by default.

It is unlikely that the card is capable of running Google Earth satisfactorily with Ubuntu.  You might get some improvement by using a lighter DE such as XFCE, buth that is not terribly likely.

---

### Post by Yellow Pasque on 2017-09-03
You already have the correct driver loaded, and it's the only accelerated driver available. If you can't run GE to it's fullest ability, it may be because your GPU isn't very powerful. Although it meets the minimum requirements AFAICT, I don't know if newer versions of GE upped the requirements.

---

### Post by jack6128 on 2017-09-04
Thanks, people. Looks like I might need a new machine.

---

### Post by Yellow Pasque on 2017-09-04
Well, it could just be a bug. I mean, assuming you have the free disk space (500MB), your system meets the minimum requirements.

This is what I found:
> For a minimum requirement, it requires a Kernel of 2.4 or later, CPU of at least Pentium 3 with 500MHz speed. System memory or RAM must also be at least 512MB or higher. Take note of the hard disk space, which must be at least 500MB free. You also have to use at least a DirectX 9 and 3D capable graphics card and 64MB of VRAM, aside from the 1024x768p of screen resolution.
    
For the recommended setup, the Kernel 2.6 or later is needed. System memory or RAM should also be at least 1GB. Free hard disk space must reach at least 2GB and the graphics card must be at least DirectX 9 and a VRAM of 256MB. Moreover, the screen resolution must be at 1280x1024p, with minimum settings of 32-bit color in order to run Google Earth Pro flawlessly in your computer system.

---

### Post by mörgæs on 2017-09-06
You could try if you can find a DEB file for Google Earth 6. It's less demanding for the hardware.

---

