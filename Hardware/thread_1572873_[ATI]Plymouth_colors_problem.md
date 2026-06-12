---
title: "[ATI]Plymouth colors problem"
date: 2010-09-11
forum: Hardware
---

### Post by bel3atar on 2010-09-11
Hey, I've installed the proprietary ATI driver for my HD5470 and managed to get higher resolution but still having a color issue at each startup :( :
[http://yfrog.com/69dscn1204ej](http://yfrog.com/69dscn1204ej)
Here's my xorg.conf
```
Section "Screen"         Identifier      "Default Screen"         DefaultDepth    24 EndSection  Section "Module"         Load    "glx" EndSection  Section "Device"         Identifier      "Default Device"         Driver  "fglrx" EndSection
```thanks

---

### Post by bel3atar on 2010-09-14
Does anyone have a similar problem??
With the standard ubuntu logo, there's some green around it.

---

