---
title: "External Monitor enabled but remains blank (black), possible desktop effects problem"
date: 2008-05-20
forum: Hardware
---

### Post by webbsd on 2008-05-20
Problem: The external monitor I use at work stays blank (black) and refuses to display anything. The light on the monitor stays orange (no signal?).

On Friday night I attempted to enable desktop effects which failed to start (I did not have the external monitor connected as I was at home). When I got to work on Monday my external monitor refuses to display anything. As I didn't find the problem for several days this might not have been the cause (possibly I changed another setting or installed an update over the weekend that I don't remember). Note that I don't want the desktop effects, I was just playing around to see what they looked like. They are currently disabled.

OS: Hardy Herron 8.04
Laptop: Toshiba A70/7001
Video Card: ATI Radeon Mobility 9100IGP
External Monitor: ViewSonic VA1912w
Native res on external monitor 1400x900

I've tried my laptop with other monitors, and the monitor on other computers, both work correctly. It is only this combination that doesn't work. I booted into ms windows to test. The external monitor works but only when I enable the composite synchronization option (- horizontal + vertical, composite enabled).

Unfortunately I've tried many things to get this to work so I've changed many settings over the last few days trying to fix this. 

What is interesting is that the screen-resolution app and xrandr can detect the monitor; however, it refuses to turn on. My desktop is extended to the correct size (the mouse moves off the screen). Also, get-edid fails (see attached get-edid.txt); however, the X server seems to retrieve the information correctly (see attached X.0.log.txt.bz2).

I have tried to avoid adding monitor sections and mode lines to my xorg.conf file as (1) it didn't require them last week for everything to function correctly, and (2) since I plug in several different monitors it would be annoying to have to mess around with the xorg.conf all the time.

I've attached my Xorg.conf file; however, this isn't the one that was working from last week. Unfortunately it was overwritten at some point (enabling desktop effects maybe, or possibly something foolish I did).


Any information/advice would be greatly appreciated. I hope I have provided all relevant info.

Cheers.

Steve.

---

### Post by webbsd on 2008-05-21
The monitor just switched on and worked for about 1 minute and then switched off again. I have no idea why.

---

