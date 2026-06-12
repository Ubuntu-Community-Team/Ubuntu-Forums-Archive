---
title: "Death to TOUCH SCREENS!"
date: 2009-01-30
forum: Hardware
---

### Post by BradTowle on 2009-01-30
Well I won't lie, when it comes to linux gurus I am not it.
However I have spent the last two days perusing forums on trying to get the touchkit software to work.

I have a 15 touch screen I am trying to interface with my laptop...yes I know this doesn't seem very useful, its for research.  I have a Dell latitude D510.  

Anyway there was a lot of talk about this software, I fixed the bug that was in the source code and I was able to get it to compile and install.  However, when I try to run the configuration tool I get:

btowle@Ragnarok:/usr/bin$ sudo ./touchcfg
[: 9: ==: unexpected operator
can not open display


Apparently only one other person on the entire internet has ever gotten this error, so I feel special.

What I have tried to do:  I changed the name of the USBtouchscreen.ko so it would not interfere with the tkusb.ko that touch kit installs.  (Ironically I was able to get some responce from the default)  

I have manually walked through the installation and I know the boot up script is running.

The only part that has me completely baffled is the ports.  If I do a fresh install (Make install) I have will find two files in my /dev, one will be tkpanel0 and the other tkpanel1.  This is good, this is what the software is suppose to use.  However when I restart, and yes even if I run the scripts manually these to ports are not created at all.  Does anyone know if TouchKit has another script it has to call, I am using these three commands to invoke it.
	insmod /usr/local/TouchKit/tkusb.ko
	/usr/bin/usbpnpd
	/usr/bin/tpaneld

I know for sure the first one is working on boot up, I have no way of telling if the other two are working.  These commands are in rc.local.

Any help would be awesome, thanks guys
Brad

---

### Post by BradTowle on 2009-01-30
Alright, well as of last post, I explained that the driver creates a file called
/dev/tkpanel0 however when I restart I do not see this file.  After trying some random stuff I diabled usbhid and low and behold /dev/tkpanel0 was there when I bootedup.  Of course nothing on my usb worked but the correct driver was there.  

So what is usbhid doing, and why will it not allow my rc.local script to run?  I did not disable the universal usb controller so I don't understand why nothing on my usb drive would work?

Cheers
Brad Towle

---

