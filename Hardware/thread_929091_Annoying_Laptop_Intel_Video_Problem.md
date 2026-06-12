---
title: "Annoying Laptop Intel Video Problem"
date: 2008-09-24
forum: Hardware
---

### Post by jackocleebrown on 2008-09-24
I have a very annoying issue that I have been unable to resolve - I must not be alone with this!

System is a fairly new HP laptop with an intel g45 chipset and integrated graphics. All great as the drivers are open source - everything works stunningly but I have a configuration problem.

I use an external display when I am at work. I have a dual head setup and this is easily setup using either xrandr or the appropriate configuration in xorg.conf. When I am not at work I do not have an external monitor 90% of the time. The problem is this:

With external monitor attached:
External display = monitor 0
laptop LVDS display = monitor 1

With no external monitor attached:
laptop LVDS display = monitor 0

So I setup my panels in gnome just how I want them on my laptop display but when I boot with the external display attached the panels appear on the external display.... so I move them back to the laptop.... so next time I boot without the external display they are not shown (as they are on monitor 1 and the laptop display is monitor 0 now)

This is driving me mad! there must be a configuration option for xorg to set which monitor is 0 and 1. I have trawled the intel driver manuals over and over. Please help me!

Thanks, Jack.

---

### Post by jackocleebrown on 2008-09-29
Ok, no replies and nothing found online... so probably only me with the problem.

As a work around I have made a script to detect when an external monitor is present and put the panels on the correct monitors in each case. Added this to session startup - not bad, it is only the login screen which is not in the right place now.

```
#!/bin/bash


if xrandr | grep "VGA disconnected" -q
then
	gconftool-2 --set /apps/panel/toplevels/bottom_panel_screen0/monitor --type Integer 0
	gconftool-2 --set /apps/panel/toplevels/panel_0/monitor --type Integer 1
	gconftool-2 --set /apps/panel/toplevels/panel_1/monitor --type Integer 0
else
	gconftool-2 --set /apps/panel/toplevels/bottom_panel_screen0/monitor --type Integer 1
	gconftool-2 --set /apps/panel/toplevels/panel_0/monitor --type Integer 0
	gconftool-2 --set /apps/panel/toplevels/panel_1/monitor --type Integer 1
fi
```

Cheers, Jack.

---

