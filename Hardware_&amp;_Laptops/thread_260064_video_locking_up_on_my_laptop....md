---
title: "video locking up on my laptop..."
date: 2006-09-18
forum: Hardware &amp; Laptops
---

### Post by malefestra on 2006-09-18
Hi everyone.  I've had this problem for quite awhile now.  When I was running Breezy, opening a video in anything but mplayer would totally lock up my laptop.  It would freeze, my cursor would go away, it would flash to black, then to a weird multi-colored version of my desktop, then black, and flash away until I did a hard reboot.  After I upgraded to Dapper, even mplayer doesn't work.  I just tried to open Gxine movie player (without opening a video - just the program) and the same thing happens.  

My graphics card is an Intel 915GM integrated card.  Any help with this would be greatly appreciated, I've been trying to make it work forever.

---

### Post by george_apan on 2006-09-18
Are you sure this isn't a harware problem? Have you tried any other distributions?

Also, have you tried any other vo modes with mplayer? Try playing a video with 'mplayer -vo xv video.avi' or 'mplayer -vo x11 video.avi' or any other mode. You can chech the available modes with 'mplayer -vo help'

---

### Post by malefestra on 2006-09-18
george_apan - 

I haven't tried any other distros - I'm trying to get it figured out before I do that, but if I have to, I will.  

Of the ones you gave me, the following will play: caca, aa, but of course that looks odd.  The "gl" option will also work and that plays video - the first time I've seen it in awhile!  How do I make that the default option for all players?

---

### Post by george_apan on 2006-09-18
It's strange that none of the other X11 modes won't work. Anyway you can make gl the default in mplayer if you open (or create if it doesn't exist) the ~/.mplayer/config file and add this in:
```
vo=gl
```
In vlc you can go to Preferences, click the Advanced options button, and then select the Video/Outpup modules and choose OpenGL. There should be something similar in gxine or xine too.

---

