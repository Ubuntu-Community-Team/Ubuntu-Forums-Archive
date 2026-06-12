---
title: "Backlight of Sony Vaio laptop doesn't work [ VGN-FZ31E ]"
date: 2010-08-21
forum: Hardware
---

### Post by ccc2007chaos on 2010-08-21
So... I 've been tired searching and searching on internet and nothing specific appears to solve the following problem. :-(

I use a Sony Vaio laptop. The model is the VGN-FZ31E. To not make someone searching what is the graphics card, I tell you it's the NVIDIA GeForce 8400M GT.

The problem is that I can't control in any way the screen's backlight. Not the brightness of the appeared objects on the display but the light. One more hint is when I plug out the DC adaptor and the laptop continues on battery mode, although the "Reduce backlight brightness" in power manager is checked, the backlight brightness does not reduce.

I booted with Ubuntu 10.04 from a USB flash drive and the backlight brightness could be increased and decreased. So this tells me that it can work. The problem is how. I use now Ubuntu 10.04 and this was updated from Ubuntu 9.10 at least, but I don't remember if it was updated to 9.10 from 9.04. When I say update from 9.10, I mean without format. Just update from the update manager.

Hope someone helps...!

---

### Post by ccc2007chaos on 2010-08-23
No one can help? It's important to find how to make it work without format.

---

### Post by ccc2007chaos on 2010-09-02
Well, after some troubles with updating the graphics driver and for some moments having no nvidia drivers installed, the backlight worked successfully. but the troubles went away by finally installing the drivers and the backlight stopped working again.

So i believe that the problem has to do with the graphics driver and the vaio laptops. As nvidia , for windows, the model i have ( vgn-fz31e ) and generally sony vaio is not supported. I suppose that sony has configured the gpu in an other way that was meant to be for nvidia. strange things. is there any solution finally?

---

### Post by benste on 2010-09-21
HI ccc, just wanted to let you know that the NVIDIA closed source driver doesn't integrate into the whole system very well.

the only way diming the screen is to install nvclock and use "smartdimmer -s [15-100]" to set a value.

If you use the nouveau open source driver you'll have a better integration but no 3d arceleration yet.
Suprisingly even this stopped working in maverick (upcoming new version), but it will be hopefully back in there for release.

---

### Post by ccc2007chaos on 2010-09-21
benste... thank you soooo much!

---

### Post by benste on 2010-09-21
btw. if you want to support this procedure, you may supscirbe to the bug report or mark your self as affected within LP bugs:

e.g.
[https://bugs.launchpad.net/nouveau/+bug/644522]("https://bugs.launchpad.net/nouveau/+bug/644522")

---

