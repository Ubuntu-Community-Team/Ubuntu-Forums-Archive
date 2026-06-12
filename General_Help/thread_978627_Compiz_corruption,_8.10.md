---
title: "Compiz corruption, 8.10"
date: 2008-11-11
forum: General Help
---

### Post by rosyatrandom on 2008-11-11
Hi, I'd been having a few issues since upgrading to 8.10, so I decided to do a fresh install - using the 64-bit version this time, just to be sure.

The problem I have now occurred when I rebooted the system for the first time - the screen draws OK, but every time it redraws an element it is horribly corrupted. I have attached some screenshots to show what it looks like.

The problem is definitely to do with Compiz (which had been running fine before the restart); if I Alt+F2 'metacity --replace &' to use metacity instead, I have absolutely no problems. If I just Alt+F2 'compiz' I get a quick redraw showing the screen again before it quickly corrupts again.

I am running on an Acer Travelmate 4230 (now with 4Gb of memory). The graphics card reads as 'Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)' However, I should note that I had previously tried Kubuntu 8.10 before adding the memory and had encountered the same issue then. At the time I put it down to having installed ubuntu-desktop and it causing problems with the KDE session.

---

### Post by eternalnewbee on 2008-11-11
Is your graphic card enabled?
You can check in: **Main Menu > System > Administration > Hardware Drivers**, and see whether or not it's activated.
EDIT: enabled = activated

---

### Post by rosyatrandom on 2008-11-11
It comes up empty; the only message is 'No proprietary drivers are in use on this system'

---

### Post by eternalnewbee on 2008-11-11
> using the 64-bit version this time
Did you use the 32-bit version in Hardy? (assuming you used Hardy)
Maybe that's the problem...
> It comes up empty; the only message is 'No proprietary drivers are in use on this system'
So that would've been the same in your previous version.

---

### Post by rosyatrandom on 2008-11-11
Yeah, last time I was on the 32-bit one. I mainly changed in order to have the best chance of utilising the extra memory. Hope there's a fix, though; having Compiz is quite nice!

---

### Post by eternalnewbee on 2008-11-11
> Yeah, last time I was on the 32-bit one. I mainly changed in order to have the best chance of utilising the extra memory. Hope there's a fix, though; having Compiz is quite nice!
Maybe 32-bit is your best option?

---

### Post by rosyatrandom on 2008-11-11
I really don't want to have to reinstall everything all over again. Too much configuring! And besides... what if it's an 8.10 issue rather than a 64-bit one?

---

### Post by rosyatrandom on 2008-11-25
I've solved the problem, people! At least, I seem to have.

I ran compiz from a terminal, and noticed the following:
```
/usr/bin/compiz.real (bicubic) - Fatal: GL_ARB_texture_float not supported. This can lead to visual artifacts.
```

So I disabled the bicubic plugin and everything's working fine.

---

