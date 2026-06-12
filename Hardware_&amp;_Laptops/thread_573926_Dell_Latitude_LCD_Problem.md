---
title: "Dell Latitude LCD Problem"
date: 2007-10-12
forum: Hardware &amp; Laptops
---

### Post by c0re on 2007-10-12
I have a dell Latitude C840 and have completely switched over to Ubuntu. Theres a problem though, with my LCD(internal). On Windows I had to use LaptopVideo2Go's custom driver enhancer to get compatibility with my screen. The LCD is a Samsung SEC3255, and commonly found in Dell computers.

[http://www.laptopvideo2go.com/enhancer](http://www.laptopvideo2go.com/enhancer)
This is the enhancer, if you look down till you find the "Enable LCD SEC3255 to properly view 1600x1200." This is the fix I need. I would usually just add the line to my ini, but since im new to Ubuntu, I don't know how. Would this be acheived by custom modelines? The fault is the driver, when i use the nvidia-legacy driver (i have a gf4 440), I cant use the full lcd, the pixels on the outside either mirror the desktop or are scrambled.  I'd like to get 3D Effects working, but I can't stand not being able to use the whole LCD.

Thanks, Josh

---

### Post by c0re on 2007-10-13
I take it nobody knows how to fix my problem?

---

### Post by it.henrik on 2008-02-08
The fix is to use this line in your xorg.con 
Option "CustomEDID" "DPF-0:/etc(X11/nvnew.raw"

If you google on it youll find more info and the file you need

---

