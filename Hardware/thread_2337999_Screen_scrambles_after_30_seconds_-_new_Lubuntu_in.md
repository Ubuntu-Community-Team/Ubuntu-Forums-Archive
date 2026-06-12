---
title: "Screen scrambles after 30 seconds - new Lubuntu install"
date: 2016-09-23
forum: Hardware
---

### Post by vbsql7 on 2016-09-23
[COLOR=#242729][FONT=Arial]My Lubuntu 16.04.01 adventure is off to a rocky start. I got it installed using the 'Alternate' (non-graphical) install on an old PC that was running Windows XP before. The screen was stable under XP but now it scrambles about 30 seconds after I log in, regardless of what I am doing.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I think I have an nVidia card in it. Not sure because I can't keep the screen up long enough to get a version number off it.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I tried lowering the resolution to a couple of different settings, but they don't seem to 'stick.' Not really sure if that would make a difference anyway, if the driver is not right.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I managed to get through step 1.1 of this article to update the software:[https://sites.google.com/site/easylinuxtipsproject/first-lubuntu](https://sites.google.com/site/easylinuxtipsproject/first-lubuntu)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]What would you try next?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I'm new to Lubuntu but can run terminal commands if needed -- and if they're short! :)

Output of lspci attached. [ATTACH=CONFIG]271331[/ATTACH][/FONT][/COLOR]

---

### Post by vbsql7 on 2016-09-30
Any recommendations? I can't read the display even long enough to play around with stuff so I need a targeted strike or a script to run or something.

---

### Post by mörgæs on 2016-10-03
Unfortunately Nvidia 6100 works better with closed-source drivers. I recommend that you do a fresh install of Lubuntu 16.04.1 using the standard ISO and that you click yes to closed-source drivers during the install.

---

### Post by vbsql7 on 2016-10-03
Thanks, mörgæs. I don't remember seeing that option but I'll give it a try! :)

---

### Post by mörgæs on 2016-10-03
Good, please post the results.

---

### Post by vbsql7 on 2016-10-07
Ok, I tried a fill Lubuntu install from CD this time.

Unfortunately, I can't get far enough to change or select any video drivers during the install. After the language selector comes up and I confirm English as what I want, the process continues on until the blue-red geodesic background appears... and at around the 2 minute mark the screen scrambles.

It was this screen issue that  made me try the 'alternate' install before. 

Is there a super-small version of Ubuntu (or any Linux) that will allow me to fix the video drivers first and then come back to the larger install?

---

### Post by vbsql7 on 2016-10-07
LXLE looks very small and designed for older machines. Gonna give that a try. [https://sourceforge.net/projects/lxle/](https://sourceforge.net/projects/lxle/)

---

### Post by vbsql7 on 2016-10-07
No joy from LXLE install. After the terminal listing of services loaded goes by, it scrambles the screen as before. 

Looks like anything graphical causes the screen to go haywire. 

Suspect what I need to do is:
1. Load non-graphical Linux version
2. Determine proper NVIDIA driver for my hardware
3. Load driver manually from terminal
4. Install (or just run) windowed desktop env

I'll quickly exceed my depth at the Linux command line. 

Suggestions?

---

### Post by QIII on 2016-10-07
Given your repeated description that the problem starts some time after the machine is running, I suspect a thermal fault in your hardware.

Your GPU may have been on its last legs when last you used Windows.  If so, you can't count on the fact that it worked tthen as an indicator that it should work now.

Laptop or desktop?

---

### Post by vbsql7 on 2016-10-07
It's a floortop. :)  I would go with the thermal theory if the failure wasn't so consistent or if it only happened from a cold power up. But I've left the machine on for hours and the behavior is the same. The scrambled screen occurs shortly after graphical operations begin. Never during the DOS or Terminal startup ops.

I'm sure I've passed the ROI point on this, but I hate to junk it if I can fix the problem with a driver.

[FONT=Verdana]Screen shot of the aftermath of the scramble attached. 

[/FONT][ATTACH=CONFIG]271535[/ATTACH]

---

### Post by vbsql7 on 2016-10-07
Some progress. Created a bootable DVD of Porteus, which lets you specific in advance (before download) that you want to boot to the command prompt and not into a graphical interface.
No screen issues after hours of being up and running in text mode.

So, now I have to figure out how to launch the window manager and see what happens next! :)

---

### Post by mörgæs on 2016-10-10
I would expect the text-only interface to work for all distros. The interesting part is whether the GUI works also.

---

### Post by vbsql7 on 2016-10-12
Taking up this discussion in the Porteus forum.
[https://forum.porteus.org/viewtopic.php?f=81&t=6297](https://forum.porteus.org/viewtopic.php?f=81&t=6297)

---

### Post by mörgæs on 2016-10-14
If you are still considering Lubuntu then 16.10 is out now. Worth trying this one too, again with closed-source drivers.

---

