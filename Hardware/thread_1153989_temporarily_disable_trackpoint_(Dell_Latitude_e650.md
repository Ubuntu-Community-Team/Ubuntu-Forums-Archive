---
title: "temporarily disable trackpoint (Dell Latitude e6500)"
date: 2009-05-09
forum: Hardware
---

### Post by AopicieR on 2009-05-09
Edit2: I found a much better solution at [http://kevin-read.com/blog/2009/10/11/disable-dualpoint-stick-dell-latitude-e6500/](http://kevin-read.com/blog/2009/10/11/disable-dualpoint-stick-dell-latitude-e6500/)

Edit: Ok, I use the following little script now:
> 
#!/bin/bash
X="$(lsmod | grep psmouse)"
if [ -n "$X" ]; then
	modprobe -r psmouse
	exit
fi
modprobe psmouse

It works ok, disabling the mouse if it is active and enabling it otherwise. I've defined a key shortcut that calls this script after adding it to the sudoers so that it can be run without entering a password.

Hi,

I have a Dell Latitude E6500 which has both a trackpoint and a touchpad. I used to disable my touchpad with synclient TouchpadOff=1, but that stopped working with the new xorg. Now I've discovered syndaemon -i 1 -d which is even more convenient as it disables the touchpad while I'm typing. Is there something similar for the trackpoint? If there is no such daemon is there any way to disable it temporarily by hand? I don't use the mouse very often and sometimes I accidentally touch the trackpoint while typing which is annoying. I'm not running a desktop environment so a terminal solution would be nice.

PS: Ok, unloading the module "psmouse" works. But maybe there is a better solution.

Thank you very much.

---

### Post by mgol on 2009-10-10
> **tantris said:**
> 
PS: Ok, unloading the module "psmouse" works. But maybe there is a better solution.
Thanks a lot! I hate Dell TrackPoint (or whatever it's called), it sometimes moves my mouse during writing...

However, I'd also very welcome any solution to turn off a TrackPoint, but not a touchpad - sth like this synclient command which does the opposite.

**EDIT:** One more question: how to disable this module automatically at start? (or better - not to load it at all) If I really want a touchpad, I can manually load the module in in tty1 terminal...

---

