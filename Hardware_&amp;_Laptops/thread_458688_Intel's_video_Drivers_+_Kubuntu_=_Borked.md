---
title: "Intel's video Drivers + Kubuntu = Borked"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by Cogman on 2007-05-29
Hey, I have an Acer Travelmate 2300 (with Intel's 855GM Integrated graphics card). By default, Kubuntu will use the i810 drivers.

I want to get max performance from my video card and from what I have read, intel's drivers are the way to go.  When I install the package (xserver-xorg-video-intel) Kubuntu will get to KDM and then crash when I try to log in. I can get in via failsafe session.  When I try to revert back to the i810 drivers, X fails completely and I have to resort to a full reinstall of kubuntu (Really, I cant tell you what is going on there).

I have tried changing xorg.conf to intel rather then i810 for the driver, no dice.  The strange thing is that I have been able to use the intel drivers in regular ubuntu (though it is unstable, does not like xrandr operations)

I have no fear of compiling the package from source, but I failed at my first attempt (it was complaining about Xinearama), so if that would give me better results, just tell me what packages I will need to compile (besides the basics like make and gcc).

In summary, I have kubuntu 7.04, and want to use intel's drivers for 855GM graphics card. it does not work, what do you guys suggest doing?

---

### Post by Cogman on 2007-05-30
*Bump* still haven't figured it out.

---

### Post by hmistry on 2007-12-11
I will be doing something similar soon with a G33 based board. When I tried this on Fedora I had xinerama related issues and had to install xserver-xorg-sdk IIRC.

---

