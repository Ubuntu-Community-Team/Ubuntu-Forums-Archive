---
title: "Serial Mouse not recognized in Xubuntu 9.04"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by DNP on 2009-04-24
My serial mouse does not work in Xubuntu 9.04.  I made the following changes to the  xorg.conf file but the mouse still does not work even after rebooting:

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/ttyS0"
Option "Protocol" "auto"
Option "ZAxisMapping" "4 5"
EndSection

These changes did work on for me in unbuntu 8.04, but since version 8.10, they have not.  It looks to me like the xorg.conf file is not used any more, since it was more or less empty when I first opened it.

The mouse has worked for many years in Windows XP, so the mouse is not the problem.

If any of you know how to fix this problem, it would be greatly appreciated.

Thanks.

---

### Post by ivgelder on 2009-10-09
I have the same problem. Does anyone know a solution?

---

### Post by Mark Phelps on 2009-10-10
Don't mean to discourage you, but I had the same problem with a serial mouse NOT being detected in Xubuntu 8.10 and despite reading LOTS of posts in the Hardware subforum, was not able to find anything that worked.  Had to resort to plugging in a small USB hub into the sole USB port and using a USB mouse.

---

### Post by racie on 2009-11-27
Change the line
```
Option "Protocol" "auto"
```
to
```
Option "Protocol" "Microsoft"
```

---

