---
title: "How do i find out what graphics driver is running?"
date: 2009-09-08
forum: Hardware
---

### Post by ssouffri on 2009-09-08
[LIST=1]
[*]I want to know what graphics driver is running. In opensuse I could see it in xorg.conf but kubuntu's xorg.conf file is very empty. Preferably not via a gui and as distribution independant as possible.
[*]Can anyone also point me to a utility to change which driver will be used? In opensuse I used sax2.
[*]If the xorg.conf file is so empty how is the xserver configured?
[/LIST]

---

### Post by hal10000 on 2009-09-08
I assume you have an ATI graphix card.
If you can't find a line
```
Driver "fglrx"
```
then you have just the standard driver loaded.
To install the hardware-accelerated driver try to run [COLOR="Red"]jockey-kde[/COLOR]
and look for your fglrx driver.

---

### Post by arcull on 2009-09-08
you could use glxgears command to see the number of frames per second, if it is around 200 FPS, then you don't have the correct driver.

---

### Post by wojox on 2009-09-08
```
lspci | grep VGA
```

---

