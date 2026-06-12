---
title: "[SOLVED] How do I send the second window to a second screen?"
date: 2008-09-07
forum: General Help
---

### Post by DouglasAWh on 2008-09-07
I have this problem in both Firefox and OOo. If I open one up and I want a new window for a second document or just to have to webpages up at the same time, I can't drag it on the second monitor.  If I drag, it goes to another workspace. Is there a way to do this; some sort of command line switch to force the second window to go to the other monitor? I'm using an old high-end nVidia graphics card on Ubuntu and I'm using two X sessions, not TwinView, because the two monitors are different.  Thank you for your help!

If you're here looking for answers to my question, you might also check out [http://answers.yahoo.com/question/index;_ylt=An2MdT14VolXvYOwJttJknTsy6IX;_ylv=3?qid=20080907135335AA5LXE7](http://answers.yahoo.com/question/index;_ylt=An2MdT14VolXvYOwJttJknTsy6IX;_ylv=3?qid=20080907135335AA5LXE7)

---

### Post by ryanhaigh on 2008-09-07
This is not an issue with firefox or open office but your graphics setup. If you start an instance of firefox in one X session it is bound to that X session, you can't move windows between x-sessions.

I would suggest that you take another look at twinview, having different monitors won't cause any problems and your workspace will be more flexible. As always when messing with your X configuration make a backup of /etc/X11/xorg.conf before you start.

---

### Post by DouglasAWh on 2008-09-07
> **ryanhaigh said:**
> This is not an issue with firefox or open office but your graphics setup.

I never said it was anything but a graphic set up,  I didn't like the way TwinView looked with the big GNOME bar at the top.  I was having some issues with compiz and KDE playing nice together.  I know a while back with VNC someone was trying to get me to put it on different screens using the screen number.  It never worked, but I've come a little ways in my Linux expertise since then, so I thought might there would be something similar I could do with other programs aside from VNC.  I guess for the time being I'll just install AbiWord to write this document, but it seems kind of ridiculous that I can't move it between monitors like I can work spaces.

---

### Post by ryanhaigh on 2008-09-07
The long panel issue with twinview can be resolved by adding metamodes to your x configuration, as discussed here: [http://ubuntuforums.org/showthread.php?t=771501&page=2](http://ubuntuforums.org/showthread.php?t=771501&page=2)

---

### Post by alarme on 2008-09-07
Try installing nvidia-settings from synaptic.
Disable Compiz (System, Preferences, Visual effects)
Backup /etc/X11/xorg.conf.  If things goes wrong, restore this backup.
run nvidia-settings as root
Enable Xinerama
Configure the extended desktop
Press "Save to X Configuration file" button
Restart X  (Ctrl-Alt-Backspace)

I have one NVidia 8600 GT whit a 24" LCD at 1920x1200 and 19" CRT at 1280x1024 working as 3200x1200 extended desktop

Suerte

---

