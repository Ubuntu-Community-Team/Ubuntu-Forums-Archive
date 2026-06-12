---
title: "Brightness Issue- possibly Jupiter's fault?"
date: 2011-10-17
forum: Hardware
---

### Post by Pragu on 2011-10-17
Hello all, 
I've been trying to cut down on power usage on my 11.04 eeepc netbook, so yesterday I installed Jupiter. It didn't appear to do anything, and for whatever reason it was eating up my ram, so I uninstalled it. Post restart, I can not adjust my brightness. When I hit the function key to lower brightness, the screen lights up to maximum brightness, then refreshes after a few seconds to a darker setting, but not the one i chose.

Is this some kind of bug, and is there any way to regain control of my brightness?

---

### Post by Pragu on 2011-10-20
Additional information-
I've tried installing and uninstalling jupiter, jupiter with eee support, eee-control, gnome-power-manager, and ubuntu-desktop to no avail. 
When I hit the lower brightness key (Fn+F5) the brightness changes rapidly front light to dark to light cyclically, and the notify-osd box comes up but only displays the brightness at the maximum level. 
When disconnected from the power cord, the screen flashes when i don't touch anything for about 30 seconds, then flashes again when i wiggle the mouse. 
When i boot up, the the brightness flashes about 4-5 times. it also flashes on the GDM login screen sometimes. 
Running "sudo setpci -s 00:02.0 F4.B=10" changes the brightness for a while, but it snaps back up after a little bit.
I'm thinking now a fresh install may be my only option. has anyone heard of this problem?

---

