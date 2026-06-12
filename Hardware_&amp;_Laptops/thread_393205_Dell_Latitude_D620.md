---
title: "Dell Latitude D620"
date: 2007-03-25
forum: Hardware &amp; Laptops
---

### Post by jetsaredim on 2007-03-25
I just downloaded the latest Kubuntu Feisty Beta1 on Friday in hopes of reinstalling my laptop from Gentoo.  Anyway, when I booted it, the system seems to come up all the way, but I'm neither presented with a terminal or a wm to start an install.

Anyone got any ideas?  I know the wireless won't work since its part of the linux-restricted-modules (ipw3945), so it's plugged into the wired.  I'm thinking there is some problem with the video or something, but I can't figure out what.

Any thoughts?  I was going to try downloading Edgy and give that a go, but I wanted to see if Feisty would work first.

Thanks,
jared

---

### Post by solar george on 2007-03-25
It would be better to try edgy first unless you're used to using ubuntu. Any way, try using the alternate cd, the xorg install seems to detect graphics hardware better than the live cd.

---

### Post by sean on 2007-03-26
Neither Edgy nor Feisty boot graphically with X for Dell Latitudes D620.  It is a real pain.  You have to drop to the shell and install the 915resolution package and then restart X.  For some reason neither Feisty nor Edgy bothered to include it but Dapper does.  In general, Ubuntu laptop support is painful.

Even after you get 915resolution working and you could install Feisty.  Rest assured that wireless on a Brodacom 43xx chipset is broken in a bad way.  

The only way I have gotten any Ubuntu distribution to work with a D620 is to first install Dapper.  I later upgraded to Edgy but I would not touch Feisty with a ten foot poll at this point.

Sean

---

### Post by Zed on 2007-04-06
I just booted the Ubuntu Feisty Beta LiveCD on a D620. Wireless worked out of the box; it booted into 1440x900, but in 16 colors and with the nv driver.

---

### Post by Curdsy on 2007-04-18
I also installed the Feisty beta with everything working out of the box except the resolution was set at 1024x768. Installing 915resolution did not help as it does not list the screen's native resolution. Other than that it works flawlessly. (It allowed me to load a higher resolution than its supposed native that works great)

---

