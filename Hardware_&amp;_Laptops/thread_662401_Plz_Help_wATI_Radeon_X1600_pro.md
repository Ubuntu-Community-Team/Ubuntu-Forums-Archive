---
title: "Plz Help w/ATI Radeon X1600 pro"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by big dizzle on 2008-01-08
Hey all,

I'm using ATI Radeon x1600 pro w/AMD 64 and ubuntu 7.10.  I have two monitors, but I am having trouble getting the default Ubuntu driver (vesa) to set up dual monitors.  One thing I tried was installing the driver from ATI, but whenever I restart after installing an ATI driver, the Ubuntu loading screen comes up, and then the screen goes black and nothing happens.  To remedy that problem, I reset the driver to vesa using
```
dpkg_reconfigure xserver-xorg
```
from Ubuntu rescue mode and that gets it going again but ultimately just gets me back to my original problem of not being able to use the dual monitor setup.  I also tried installing the drivers using Envy, but that produces the same results.  When I tried to install the driver myself, I used the most recent version off of ATI's website (8.443.1) and I'm not sure what version of the driver envy installed, but they both had the same result.  Any suggestions on how to fix this would be much appreciated.

Thanks,

dizzle

---

### Post by big dizzle on 2008-01-12
little addon...i've tried every method I could find posted on the forum to get this to work, and before I do the system restart, I am given every reason to believe that the driver was installed properly (when I try to install/update the driver in the kernal, i get a message basically saying that i have the most recent version of the driver, i also enable the driver using the restricted drivers application), but for whatever reason, I always have the same problem.  

if you don't know how to make the ati driver work, is there anyone who can recommend a different driver than the vesa driver which could possibly allow me to use dual monitors?

What about making the vesa driver work?  Whenever I try to set up dual monitors w/the vesa driver, the desktop automatically goes into low graphics mode. 

I have no idea why any of this is happening.  The default vesa driver displays a nice 1280x1020 display on both of my monitors, but it is just an identical display, and not two separate screens.  In other words, if I only wanted to use one monitor, I wouldn't be whining...

---

### Post by big dizzle on 2008-01-14
i read on another thread ([http://ubuntuforums.org/showthread.php?p=4132693#post4132693](http://ubuntuforums.org/showthread.php?p=4132693#post4132693)) that w/an asus mobo, if you have too much ram the problems i've been having are the result.  i've tried pulling out some of my RAM and then trying to use the ATI drvers and I still get the same result...plz someone help me, this is driving me crazy.

---

