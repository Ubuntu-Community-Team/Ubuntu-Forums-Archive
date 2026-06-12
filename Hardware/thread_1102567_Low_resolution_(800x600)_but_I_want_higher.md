---
title: "Low resolution (800x600) but I want higher?"
date: 2009-03-21
forum: Hardware
---

### Post by bukormen on 2009-03-21
I am new to Ubuntu and the thing that really annoys me is that the screen resolution is very low. (800x600) In windows the resolution was a lot higher. Anyway this means everything is very big. By mistake I changed the resolution to (600x480), but when I tried to revert it back to (800x600) this was impossible as the box was to big for the screen. I had to reformat the harddrive and reinstall the OS. (I have done this 3 times now after making some minor mistakes... And in the process I have lost Vista!)

Does anyone know how to change the resolution? I have a ProNitron 17/300 monitor. I do not have a driver for it.

---

### Post by Possum Films on 2009-04-13
I am quite surprised that Ubuntu used 800x600 resolution on your monitor. I would have expected that Ubuntu would have used a resolution of at least 1024x768 on a monitor that it didn't recognise (and if it did recognise your monitor, it would have certainly used a higher resolution).

If a window is too big to fit on your screen, you can move it by holding down the Alt key while you click and drag on any part of the window. 

If you can't find the screen resolution that you need from the display properties box, try running this in the terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And then restart.

---

