---
title: "screensaver and &quot;put display to sleep&quot; don't work with external monitor"
date: 2010-11-03
forum: Hardware
---

### Post by Schuby007 on 2010-11-03
Hi,

I've installed Ubuntu 10.04  64-bit on my Alienware m15x laptop. The laptop has an Nvidia GeForce  8800M GTX gpu; I'm using NVIDIA Driver Version: 195.36.24 (recommended  by "Hardware Drivers").

I use my laptop at home for the most part where I use a single external monitor which is connected via HDMI and have the laptop display disabled with nvidia-settings.

The problem is that when I close my laptop "lid" the screen saver  and gnome-power-manager "put the display to sleep" functions stop  working on the external. It's weird, cause the external goes dark after 5  minutes (which is the delay I set for the screensaver) and it asks for  password when I  shake the mouse (which is what I want) but I don't get  the actual screen  saver nor does the display turn off after 30 minutes  which is what I set in gnome-power-management. NOTE: these two items DO  WORK when I have my laptop lid OPEN.

It seems to me that the gnome-screensaver and power management are   getting confused between my internal and external monitors. Perhaps it   could be because display settings are handled by nvidia-settings and it doesn't realize that I'm using an external monitor?? If   thats the case then I consider it bad practise for Ubuntu to include the   proprietary nvidia drivers without proper support.

I'd be very interested in knowing if anyone else is having this problem. And would be thrilled if anyone had any solutions.

Thankyou
P.S. Is there any way to disable the "lid-close" switch in Ubuntu at  least while I have my external connected. I would like the system to be  aware that I close my laptop lid when I'm using the laptop by itself,  but it seems to be a problem here when I'm using only my external  monitor.

---

### Post by Schuby007 on 2010-11-08
BUMP

Really? No one has any ideas?

---

