---
title: "Desktop Effects and nVIDIA GeForce FX 5500"
date: 2008-07-27
forum: General Help
---

### Post by NewDigger on 2008-07-27
I've been trying to get Desktop Effects working since I installed 8.04.1.
I've updated everything, and tried various drivers but can't get it to work.

I have an nvidia driver listed in "Hardware Drivers" however, when I enable it and reboot, my screen is messed up. Colours aren't right, and randomly changing, things like that. Nor is the screen resolution correct.

I also tried using EnvyNG to get the right drivers which would allow me to enable Desktop Effects but they did not work.

I did manage to install nVIDIA drivers which appeared to work using EnvyNG when I manually selected the 71.86.04 version drivers. However when I tried to enable Desktop Effects I got an error saying something about composite effects not being available.

Anyone got any ideas how I can fix this?

---

### Post by Mgiacchetti on 2008-07-27
sudo apt-get install xchat     then in xchat join irc.freenode.net/8001

/join #ubuntu     

you should be able to get better support there.

---

### Post by NewDigger on 2008-07-27
Been on there, no one seemed to be able to help me.
Least I waited a while, and no one seemed to give any suggestions at all.

Any other ideas?

---

### Post by AnonCat on 2008-07-27
Check your xorg.conf file ( etc/X11/xorg.conf ) to see if the following lines are within it.  If they're not add them to the bottom of the file:

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

If that doesn't work let me know.  I'm using a 5500 FX card with everything working and my xorg.conf file might be useful for you. I'm using driver 173.14.09 .

---

### Post by NewDigger on 2008-07-27
I'm stuck with the oldest drivers, the others don't work right.

Did the change, and I now get a "Desktop Effect cannot be enabled" error. Also won't let me have a screen resolution above 800x600.

Anything else I can try?
Also, when I try and use the NVIDIA X Server Settings program, it tells me I don't appear to be using the X server driver?

Last time I tried ubuntu these worked practically out of the box, it downloaded the correct drivers. I'd have thought it'd have got it right again.

Anyway, any other ideas?


Also, on a side note. It wouldn't matter if I used wubi to install ubuntu would it?

---

