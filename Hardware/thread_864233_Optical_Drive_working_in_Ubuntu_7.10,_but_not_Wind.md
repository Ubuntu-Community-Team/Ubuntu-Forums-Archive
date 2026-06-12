---
title: "Optical Drive working in Ubuntu 7.10, but not Windows XP/Vista"
date: 2008-07-19
forum: Hardware
---

### Post by blacklantern on 2008-07-19
This is actually more of a Windows and Ubuntu issue, and if I've posted in the wrong place then please let me know.

For some time now, my optical drive behaves really strangely in Windows, but not in Ubuntu. At some point when I had Vista, the file browser struggled every time I tried to look through the contents of a disc, and then eventually went to a "Not Responding" state. The disc would show up in the "My Computer" screen, but when I click on it to view its contents the problems begin. Meanwhile, Ubuntu 7.10 had absolutely no problem when I used Nautilus to browse discs. 

Eventually, due to the memory issues of Vista, I downgraded back to XP, and I of course reinstalled 7.10 when I reformatted my master drive. In the back of my mind, I was thinking that maybe a reformat would solve my optical drive issue too, but even in Windows XP, I'm still seeing the same problem. I'm confused as to why, since Ubuntu is experiencing no problems whatsoever. Does anyone here who dual boots have any idea what my issue may be? A simple point in the right direction would be awesome.

---

### Post by phidia on 2008-07-19
The 1st thing that comes on me on this is device drivers-do you have the latest and correct driver installed in windows for that optical drive?

---

### Post by ljonesj on 2008-07-19
um to my understanding optical drives dont have device drivers but i could be wrong it may be its frimware that could be a issue

---

### Post by jerome1232 on 2008-07-19
Well they do have device drivers they are just pretty generic/universal, I would check for firmware updates/driver updates from the manufacturer. Maybe uninstall/reinstall the cd-rom via the device manager.

---

### Post by blacklantern on 2008-07-19
Yeah, immediately after I posted I went for firmware updates on LITE-ON's website. There was an error and the application couldn't flash the firmware in, but I'm going to start in safe mode and see if I can't make it load that way. Again, sorry to insert a Windows problem in here - I thought it would be helpful to know why there was no problem in Ubuntu but a problem in XP.

---

### Post by ljonesj on 2008-07-20
that goes to show u how much better ubuntu is for getting some stuff to work than windows sometimes that u dont have to fiddle with it as u do in other cases

---

### Post by cyber_x on 2008-07-20
check for virtual devices.. (to mount ISO's) and try to uninstall them. they sometimes mess the real drive's drivers

---

