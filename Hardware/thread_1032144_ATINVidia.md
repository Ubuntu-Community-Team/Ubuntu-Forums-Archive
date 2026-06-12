---
title: "ATI/NVidia"
date: 2009-01-06
forum: Hardware
---

### Post by ahddm on 2009-01-06
I am purchasing a new computer but can't decide what brand of video card to go with which is better supported in Linux?

---

### Post by gettinoriginal on 2009-01-06
From the reading I have been doing, it is 60/40 (approx) for nvidia, but really depends on the version.  Both can be configured to run, just depends personal preference.  You will get better results by doing a google of "ubuntuforums.org <ati "version" vs nvidia "version"> (edit for specifics)  :P

---

### Post by binbash on 2009-01-06
nvidia has far better drivers on linux

---

### Post by psihodelia on 2009-01-06
Wrong! Nvidia has not only bad drivers but also has bad defective chipsets. Their ALL(!) Linux drivers have poor 2D Desktop performance because of agreements with Microsoft. Moreover, ALL(!) GeForce 8 and GeForce 9 series cards have overheat problems - it means that if you will play long enough on max graphics settings - your Nvidia suddenly will die.

---

### Post by Cracauer on 2009-01-06
The binary NVidia driver go on my nerves, but yes what they do they do well. The major problem I have is huge amounts of physical RAM taken up by the X11 server when they are running.

The binary ATI drivers are trash.

The dri/Xorg driver for ATI, that's the real question. I started fiddling with them and they aren't quite ready to give me what I need on my X1650something, in particular google Earth and Blender. But they are getting there rapidly. But at least this will force you to run very recent Xorgs, which might not be what you want.

---

### Post by sd23ddde on 2009-01-06
Always a good source of information is the ubuntu hardware support list:

Here you can have a look on what gfx (and other hardware) is at least supported by ubuntu. Therefore you might gather a list on the cards you would by and that are supported by ubuntu (if you didn't allready):

**Hardware Support List**
[https://wiki.ubuntu.com/HardwareSupport/]("https://wiki.ubuntu.com/HardwareSupport/")

**ATI**
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti")

**NVidia**
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia")


I made good experience with NVIDIA by myself so I would suggest to buy a NVIDIA card (but to be honest I never owned an ATI card). 

Best Regards

---

### Post by linux_tech on 2009-01-06
Nvidia has seems to put more work into ensuring their drivers are Linux compatible, more so than ATI.  But before you buy any hardware, it always advisable to do a quick check of a hcl.

You can check compatability here-- [http://kmuto.jp/debian/hcl/index.cgi](http://kmuto.jp/debian/hcl/index.cgi)
[http://www.linuxquestions.org/hcl/](http://www.linuxquestions.org/hcl/)
[https://help.ubuntu.com/8.04/installation-guide/i386/hardware-supported.html](https://help.ubuntu.com/8.04/installation-guide/i386/hardware-supported.html) 
[http://www.tldp.org/HOWTO/Hardware-HOWTO/](http://www.tldp.org/HOWTO/Hardware-HOWTO/)

---

### Post by Skripka on 2009-01-06
> **Cracauer said:**
> The binary NVidia driver go on my nerves, but yes what they do they do well. The major problem I have is huge amounts of physical RAM taken up by the X11 server when they are running.

The binary ATI drivers are trash.



Yep, which is a shame-as they make very good cards/bricks, and their Windows drivers are very good...their Linux drivers are someone's homework done in the hallway 5 minutes before class started.  Thank gawd they are open sourcing their drivers, they need somone-anyone else writing their drivers.

Nvidia's drivers are actually better on Linux than in windows, in terms of what the driver tells you-and lets you adjust.

My GTX260 works beautifully.

---

### Post by ahddm on 2009-01-07
So basically comes down to both are trash drivers lol I was hoping maybe ATI would be better since they just announced open source drivers. I guess I'll wait a few months for more friendly drivers, since I want to use it as a gaming pc at same time I need good drivers

---

