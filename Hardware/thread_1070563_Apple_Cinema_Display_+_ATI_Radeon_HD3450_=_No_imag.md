---
title: "Apple Cinema Display + ATI Radeon HD3450 = No image."
date: 2009-02-15
forum: Hardware
---

### Post by milepost15 on 2009-02-15
I have a computer running Ubuntu v8.10, it has an ATI Mobility Radeon HD 3450 video card in it which I am attempting to pair with a 20” Apple Cinema Display (Aluminum).  Everything is fine during post and while Grub is doing its thing, however when the login window appears, the display shuts off.  I can see the loading screen with the progress bar, but after that... nothing.

While configuring the machine I was using a standard LCD screen connected to the Radeons VGA port which didn't work until I downloaded and installed ATI's proprietary driver from here: [http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html) that monitor works fine now, however, after some checking I discovered that that driver is not active, which I'll explain in a second.

I've been looking around for answers, and have found some information about modifying the xorg.conf file but I'm not really sure what information I need to specify for this screen/video card combination.  Adding to my confusion, when I look under “System” &#8594; “Administration” &#8594; “Hardware Drivers” I'm told that “No proprietary drivers are in use on this system”  The FGLRX driver I installed is listed there, but is not active.  When I attempt to activate it, I get a progress bar, while Ubuntu seems to do something, however that eventually disappears and the driver remains inactive.

To sum this up, I need to get the Apple Cinema Display working with this video card.  To do so, should I be using the FGLRX driver, and if so, how do I activate it/do I need to activate it?  Or, should I be using a non-proprietary “ati” driver, and if so, what one?

I hope someone can help me with this, I have some idea of what I'm doing, but I am by no means a Linux expert.

Thanks,

- Chris

---

