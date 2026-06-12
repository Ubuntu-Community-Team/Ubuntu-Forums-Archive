---
title: "Nvidia 7100 GS problems"
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by K-Zodron on 2007-07-13
Okay, so I bought an nvidia card (cheap one) because ATI's drivers are..you know, ****. Great price, got it in 2 days (I know, interesting!) :)

Then I went happily to install it on the Ubuntu Feisty computer. Well, first guess is nvidias own drivers will work. So I browse to nvidia.com, get the drivers, install them with 'sudo sh nvidia*.sh' and hit the ok's and whatnots. Everything installs fine (it seems like it) - but when I try to startx, I get the cool nvidia image and like half of a second I see X starting up - then it crashes. Bleh! :confused:

So, Internet is a great place to search stuff. I tried envy, installing, uninstalling, cleaning, whatever - just freezes in the black screen kindof and doesn't work (startx tells me nvidia module could not be loaded (it doesn't even exist!) - I tried modprobe nvidia and stuff, whatever they do) :mad:

Then I tried 'sudo apt-get install nvidia-glx-new'. I get some crap about libmesa gl's and stuff, and fails to install (dpkg error code 1 - WOOHOO!)

Mkay, so now I got the nvidia.com drivers running again - but it crashes. I tried 'cat /var/log/Xorg.0.log | grep EE' and found only 3 errors (all the same) about could not load wacom something - I've heard those errors don't matter. 

Any ideas?


**Edit:** I tried setting the driver to "vesa" and "nv" in xorg.conf but now it crashes with (EE) AIGLX: DRI module not loaded

---

### Post by tgm4883 on 2007-07-13
try sudo apt-get install nvidia-glx

---

### Post by K-Zodron on 2007-07-13
I have tried that, but the error is the same as with nvidia-glx-new - some junk about libmesa etc. :(

**Edit:** [size=7]\o/[/size] IT WORKS! :p 

1) apt-get install xorg-driver-fglrx
2) apt-get install nvidia-glx-new (maybe you can skip this xD)
3) sudo envy -t and uninstall nvidia drivers, clean the nvidia drivers, and install them again

It works! WOohoo!

---

### Post by tgm4883 on 2007-07-13
> **K-Zodron said:**
> I have tried that, but the error is the same as with nvidia-glx-new - some junk about libmesa etc. :(

**Edit:** [size=7]\o/[/size] IT WORKS! :p 

1) apt-get install xorg-driver-fglrx
2) apt-get install nvidia-glx-new (maybe you can skip this xD)
3) sudo envy -t and uninstall nvidia drivers, clean the nvidia drivers, and install them again

It works! WOohoo!

Odd, as fglrx is the ati drivers.  I would assume that it is installing a dependency

---

### Post by K-Zodron on 2007-07-13
Yeap, I had ati drivers before, maybe it messed up something on uninstall :S

---

