---
title: "Glitch seems to be related to Nvidia graphics driver"
date: 2008-08-16
forum: General Help
---

### Post by sofasurfer on 2008-08-16
In installing compiz on my "practice linux box" I installed nvidia-glx, which I did just as I did on my "working linux box". When I run ./compiz-check Linux however says " The nv driver is not capable of running Compiz, you need to install the
 proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n)" 

I click "Y" and I get the window to enable the accelerated graphics driver. When I click "enable" 
 
"E: nvidia-glx: subprocess post-removal script returned error exit status 2"

The "details" window is attached...(since this is my first attachment I can only hope it shows up)


Now when I try to install any package I get the same error messages shown.

Any ideas whats wrong?

---

### Post by lackoblacko on 2008-08-18
try installing envy

sudo apt-get install envyng-gtk

read here for more details
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

---

