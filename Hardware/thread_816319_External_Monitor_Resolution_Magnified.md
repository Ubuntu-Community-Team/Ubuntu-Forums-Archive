---
title: "External Monitor Resolution Magnified"
date: 2008-06-02
forum: Hardware
---

### Post by rste on 2008-06-02
I'm sure the answer is in this forum somewhere but I guess I don't know what words to search for.

I have a Dell M60 Laptop with an NVidia Quadro FX Go1000.  I have the external monitor mirroring the lcd display.  The problem is that the external monitor display appears "magnified".  Only a fraction of the desktop is visible at any one time.  Moving the mouse around will cause the area displayed to shift so I can pan around and see the entire desktop but only a portion at a time.  This behavior remains no matter which display resolution I choose.

FWIW
If I run nvidia-settings, under X Server Display Configuration, I cannot set the resolution of the CRT greater than 640x480.


The CRT is A 20" SGI which I use with my MacBook Pro at 1600x1200, 60hz just fine.

What do I need to do to make the CRT show the full 1600x1200 at one time?

---

### Post by Stunts on 2008-06-20
I have the exact same probelm as you!
Only I'm using an Nvidia 8600M GT.
I'm also trying to connect to a projector rather than a monitor.
Otherwise the problem is the very same.
Any ideas anyone?

---

### Post by Stunts on 2008-06-21
Hi, I have found a temporary solution for my problem, but I'm not sure you can apply it to your own issue too.
What I did was connect my laptop to a LCD monitor, which was detected correctly by nvida-settings. I disabled it and then unpluged it, and connected my laptop to the projector, and didn't click detect again, so I got to using it as if it was a LCD monitor.

Voilá!
Instant desktop projection! Worked like a charm. Of course, when I am making the official presentation I will have to have a LCD monitor next to me...

I'll have to try and get a better solution. At least I know that is can work.
I'll report back when I find a better alternative.

---

### Post by Stunts on 2008-06-21
Hi!
After some research, I have a found the source of the problem, and a workarround for the bug:
The proprietary Nvidia driver is buggy, and does not correctly detect all monitors' EDID's. Thus it just reverts to 'safe' mode - 640x480 resolution.
In order to workarround this you will have to set the resolution to "Auto" in Nvidia settings and then edit your /etc/X11/xorg.cong file.
In the screen section (probably CRT 0, your second screen), you should find a 'modline' line. Just change resolution in there to whatever you want (be sure the monitor your are using can handle it).

There you go! A fully working monitor. 
Credit for this goes to lots of forums I visited, which had the workarround for the bug.
Let me know how it worked for you!

---

