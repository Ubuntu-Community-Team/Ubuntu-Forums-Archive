---
title: "Wacom, pen works in reverse."
date: 2009-09-12
forum: Hardware
---

### Post by ofde on 2009-09-12
Hello. I have a problem with the Wacom graphire in Gimp (with inkscape works well) using Ubuntu 9.04.  
 The pen works in reverse, I mean who writes for the round, the eraser.  
 I have installed "wacom-toold" and "xserver-xorg-input-wacom".  
 I look at input devices and I get the Wacom Graphire 3, but I do not know how to solve the problem.

---

### Post by Favux on 2009-09-12
Hi ofde,

It looks like you configured the wrong input device in Gimp's extended input configuration.  See near the bottom of here:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

To see what HAL is calling your devices enter in a terminal:
```
xinput --list
```
It would probably be better if (in a terminal):
```
xsetwacom list
```
returned stylus, eraser, cursor, and pad so you wouldn't make the mistake.

To get a wacom.fdi that will parse the HAL names into linuxwacom names see post #176:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)  It will also let you use wacomcpl, the LWP's calibration and configuration gui.

Hope this helps.

---

### Post by ofde on 2009-09-15
I solved the problem changed (in Gimp), in input devices and selected _windows_ for Wacom Graphire 3.

---

