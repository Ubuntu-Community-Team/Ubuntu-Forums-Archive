---
title: "Fresh 9.04 installation and after a few minutes all fonts are garbage"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by darge0flex on 2009-05-22
As the title says I've installed ubuntu 9.04 on a fresh system (ibm thinkpad x30). Everything was fine, but after a few minutes the fonts looks more and more like black boxes. After that I've rotate between the different fonts-drawing-method's without any effect. Of course it looks best when I choose just black and white without any anti-aliasing of the fonts (look at the second screenshot). But, as you can see, in firefox are also the icons wrong.

I dont know what the reason could be. Maybe someone else here had made similar experiences?

And as I sayd it: this is a absolutly fresh installed ubuntu 9.04 without any backuped settings from an old installation.

---

### Post by jpopol on 2009-06-03
Hi there !

I had this problem as well 3 months ago when I installed Debian on my X30.

To fix this problem you just have to edit your xorg.conf file:
```
sudo vim /etc/X11/xorg.conf
```and add in the "Device" section:
```
Option     "AccelMethod"    "XAA"
```By default the Acceleration Method is [EXA]("http://en.wikipedia.org/wiki/EXA"), and was designed to replace XFree86 Acceleration Architecture.

Hope this will help !

---

