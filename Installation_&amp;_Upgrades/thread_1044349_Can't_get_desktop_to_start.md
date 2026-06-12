---
title: "Can't get desktop to start"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by treeclimber on 2009-01-19
Last night, I attempted to update my OS from 7.10 to 8.04, using Update Manager.  It wasn't finished downloading files when I went to bed, so I set it aside to allow it to continue overnight.  I woke up this morning and found out I had accidently unplugged it and it (a Dell 1505n laptop) had been running on battery and the battery had ran down.  I plugged it in.  It booted, I put in my user name and password, but then I couldn't get the desktop to open.  All I can see is my cursor.:(

I would like to figure out what to do to get the desktop to open.  Alternatively, I do have a live CD.  If I have to re-install, I need to rescue some pictures on here.  Are they in the lost+found folder?  If so, how do I open it with the live CD so I can copy them to my flash drive?  Any help will be greatly appreciated.

---

### Post by Partyboi2 on 2009-01-19
Press Ctrl+Alt+F2 to get to a terminal
then
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by treeclimber on 2009-01-20
Thanks for answering.  I could only open the desktop by using failsafe gnome.  When I used it, it said I couldn't load Hal.  I finally just did a clean install.  I got tired of messing with it.

---

