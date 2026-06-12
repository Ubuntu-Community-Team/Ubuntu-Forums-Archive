---
title: "Some graphic problem with intel 965"
date: 2008-05-21
forum: Hardware
---

### Post by sink on 2008-05-21
Dear all, I am new to Linux and ubuntu. and I try to play some game to test the graphic.

When I move the window of a game that is played in a window, the graphic of the game is painted on the desktop. 

same problem for mplayer.

also, the 3D acceleration for 3d game is very slow and hang occionally

the problem are shown in the attached picture.

thanks a lot!!!

---

### Post by sink on 2008-05-22
Have I posted in the wrong section?

---

### Post by starcannon on 2008-05-22
Try this guys guide, he was working on his desktop effects, but the trick to good 3d performance is getting the drivers set up correctly, and it sounds like he's got that figured out.

The guide is here:

[http://ubuntuforums.org/showthread.php?t=506744&highlight=intel+965](http://ubuntuforums.org/showthread.php?t=506744&highlight=intel+965)

Good Luck

---

### Post by sink on 2008-05-22
Thanks!

I have a question:

I cannot find this part in the /etc/X11/xorg.conf

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option "monitor-TV" "TVOutput"
        Option  "CacheLines"    "32768"
        Option  "DRI"   "true"
        Option  "PageFlip"      "true"
        Option  "TripleBuffer"  "true"
EndSection

---

### Post by sink on 2008-05-22
Now I know what is the problem
The desktop effects work without me doing anything.
The opengl in other application works too.

However, they do not work together.

I do not have problem when I shut down the desktop effect.

---

### Post by sink on 2008-05-22
bump.

---

### Post by DelSol on 2008-05-28
i have the same issue like you. same graphic errors with an intel gma3000. no solution so far.

---

