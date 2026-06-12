---
title: "NVidia GT 130M Issues"
date: 2010-02-09
forum: Hardware
---

### Post by dadgetboy on 2010-02-09
Hello all!

I am having an issue with the "Recommended" driver for the GT 130M on Ubuntu. I have also tried a more recent version of the the driver from the official NVidia site. Both cause my machine's screen to multiplex into six screens. I have looked at the few other posts out there concerning the GT 130M's problems, but the "NoTotalSizeCheck" workaround in "xorg.conf" did not do it for me. 

Any suggestions? 

*I know this is my first post, however I always go to these forums for help (there are so many threads on various problems and fixes that I never really need to post!)

---

### Post by dadgetboy on 2010-02-09
Text in xorg.conf:


Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

---

### Post by dadgetboy on 2010-02-10
UPDATE: Problem is now solved by using a beta driver released Feb. 5 2010 by NVidia.

---

