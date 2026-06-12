---
title: "Where does Ubuntu hide the xorg.conf file? (not the one in etc/X11)"
date: 2008-09-14
forum: General Help
---

### Post by Neo_The_User on 2008-09-14
I've been having this problem for quite some time now. I want to get my computer to boot-up in low graphics mode so I delete my xorg.conf file in etc/x11/xorg.conf and for some reason, my video works. How do I erase all xorg related files so it does not automatically detect my displays? I would like to boot ubuntu up in low graphics mode and erase the other xorg.conf file somewhere else. I did a search for xorg.conf in nautilus and nothing showed up (probably named something cute.) Any assistance to my question would really be helpful. Thank you.

---

### Post by cyclobs on 2008-09-14
as in.. change to a lower resolution?

if you need to change the resolution then you can change it in system->administration?->screen resoultion?

sorry running on memory here atm

---

### Post by Rhubarb on 2008-09-14
May I ask why you want to boot up in low-graphics mode?
Ubuntu 8.04 has bullet-proof X, so generally speaking, it should be able to detect what display you have currently hooked up, and output an optimal resolution for that display, regardless of whether the /etc/X11/xorg.conf file exists or not.

If you don't want it to detect your displays, you probably need an **/etc/X11/xorg.conf** file configured for simple generic use.
It's only when that file is deleted that Xorg tries to detect and configure any displays present.

Please explain a bit more of what you actually want to do, what video card you have, and what resolution / type of displays you have.
As most people would want Xorg to boot up in the display's native / nominal resolution, rather than low graphics mode.

---

### Post by Neo_The_User on 2008-09-14
BluBard, that really helped me understand the principles of Ubuntu 8.04's xorg.

---

