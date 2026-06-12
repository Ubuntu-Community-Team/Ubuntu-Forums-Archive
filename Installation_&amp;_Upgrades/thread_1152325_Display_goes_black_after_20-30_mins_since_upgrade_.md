---
title: "Display goes black after 20-30 mins since upgrade to Jaunty"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by BFG on 2009-05-07
Weird one this.  I updated from 8.10 to 9.04 and all went pretty well.  ATI - dual monitor, worked very well with big desktop in 8.10.

Now, even though monitor power saving is set to never and the screen saver operates OK, if the machine is left, the screens go black (not off, just black).  Nothing will bring it back.

I have enabled ctrl-alt-backspace, and this will restart a working desktop, but once the screens have gone black it doesn't work. No other shortcuts work either.

I can't remote desktop but I can telnet, so that's what I've been using to try things.

I have tried 

/etc/init.d/gdm restart
I get:
 * Stopping GNOME Display Manager... [ ok ]
 * Starting GNOME Display Manager... [ ok ]
But the display doesn't come back.

xset commands don't do anything, or complain that they can't access the display.

Any ideas?  It's really irritating having to shut down every time I leave my machine (suspend and hibernate have never worked).

---

### Post by MrsZoiby on 2009-05-09
I too am having this problem.  I turned off my screen saver and changed the power management options of putting the computer and display to sleep to never.  I just turn the monitor off if I leave my computer.  

Not sure if it's fixed, but it hasn't locked up since...  I think maybe it had something to do with my ATI card not being able to handle some of 3D screen savers.

---

