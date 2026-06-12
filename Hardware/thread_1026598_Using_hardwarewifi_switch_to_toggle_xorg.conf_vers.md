---
title: "Using hardware/wifi switch to toggle xorg.conf version"
date: 2008-12-31
forum: Hardware
---

### Post by casperlingus on 2008-12-31
_Laptop:_  Thinkpad T61p
_Ubuntu:_  Hardy Heron 8.04

I have a fairly complicated xorg.conf which sets up two monitors with one rotated, but I only need it when I'm docked.  I am in the habit of copying the correct xorg.conf to /etc/X11 before the previous shut down, in anticipation of whether I will need two monitors or not.  If I get it wrong I usually have to boot twice, as alt-ctrl-backspace doesn't necessarily reset X completely (I sometimes end up with no top or bottom panels)

Since I don't need wifi when I'm docked, I figured I could use the state of the wifi switch to determine which xorg.conf to use automatically on boot, before X is started.  This requires two things that I don't currently know:

[LIST=1]
[*] *From within a script, how do I grab the current state of the hardware-wifi switch on the front of the Thinkpad?*
[*] *Where can I insert a script that will check the state of the switch, and copy the appropriate xorg.conf version before it is read by X?*
[/LIST]

I'm assuming the script will be something of the form /etc/rc#.d/S01monitorcheck.   Of course, there may be an easier way to do this, but preferably, I'd like to know the answer to my question AND the easier way, if possible.

Thanks!
-Casper

---

### Post by tornadof3 on 2008-12-31
Putting the location of the (executable) script in the /etc/rc.local file may be a way to invoke your script in the manner you suggest?

---

