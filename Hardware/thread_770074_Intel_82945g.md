---
title: "Intel 82945g ?"
date: 2008-04-27
forum: Hardware
---

### Post by raver31 on 2008-04-27
I installed 8.04 fresh, and installed GoogleEart afterwards.
It ran like treacle.
I tested with a few OpenGl screensavers. They ran like treacle.

I checked which xserver was installed

xserver-xorg-video-intel

So, it should have supported OpenGL.

I tried changing it to both the i810 and i740 drivers.
No joy, I cannot raise the resolution past 800x600.

I am in 1024x768 at the minute using the VESA driver, but it sucks even more.

I have also tried to reconfigure the driver but this brings me to a 640x480 resolution.

There is also no cure in xorg.conf.


I am raising it here as two of my work colleagues have had the same problems, so it looks like a dodgy intel driver or dodgy opengl. Hopefully there will be an update soon.

---

### Post by raver31 on 2008-04-27
Ok, I removed the intel xorg servers and went with a stock vesa one.
I rebooted and when X started, I killed it.
I then reinstalled the intel servers and rebooted.

This time the screen came up as 1280x1170 nice.
OpenGL screensavers worked fine.
But still GoogleEarth is running like treacle.

hmmm, looks like it is a googleearth problem, but I am unsure if there has been an update to that.

---

