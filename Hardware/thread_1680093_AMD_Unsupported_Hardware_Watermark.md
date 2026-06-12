---
title: "AMD Unsupported Hardware Watermark"
date: 2011-02-02
forum: Hardware
---

### Post by Ahmed Lachheb on 2011-02-02
Guys please your help
I have an Acer Aspire 5235 BZ602 laptop and I just installed Ubuntu 10.10.
The Graphics **AMD RADEON HD 6310**. Although the HD settings work perfectly but I do have an ugly bothering watermark at the right bottom corner saying **AMD Unsupported Hardware**.
I have **ATI Catalyst Control system as the driver**.
Any help to remove this will be much appreciated.
Remember UBUNTU is Humanity to Others :)

---

### Post by devguy on 2011-02-02
[This]("http://phoronix.com/forums/showthread.php?30018-Catalyst-11.1-6870-still-unsupported") thread may be of some assistance.

Sounds like you got it working pretty well.  Can you do me a favor and see how it performs playing h.264 1080p mkv files with XBMC?  Also, I'd be interested to hear if it can run through a Unigine Heaven benchmark (I'm sure it'd be dog slow, but I'd just like to know if it has the driver capability to make it through).

Also, does sound pass through the HDMI port properly?  Interestingly, [this]("http://ubuntuforums.org/showthread.php?t=1680348&highlight=acer+522") fellah is having trouble with his onboard wireless.  I realize that he is on the Ontario APU, but both share the same Hudson chipset.  Doing an lspci command, what comes up for your wireless card hardware?

---

### Post by Droppen on 2011-04-02
I got the watermark fixed on AMD Radeon HD 6470M 

solution is: in the watermark script, instead of 
DRIVER=/usr/lib/xorg/modules/drivers/fglrx_drv.so
write
DRIVER=/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so

thread:
[http://ubuntuforums.org/showthread.php?t=1676402&page=3](http://ubuntuforums.org/showthread.php?t=1676402&page=3)

---

