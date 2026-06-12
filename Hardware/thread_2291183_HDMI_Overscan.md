---
title: "HDMI Overscan"
date: 2015-08-18
forum: Hardware
---

### Post by Lee_Henderson on 2015-08-18
Hello all, Im hoping somebody can help me.  I have a 2011 Mac Mini running Xubuntu 15.0.4, everything works and is supported.  Apart from when I connect the Mac Mini to a Full HD TV via HDMI.  It has Intel 3000 HD graphics, and there seems to be now way to control the overscan via the OS.  The menu bar at the top of the screen is cut off.  Please, is there a way to control the scan to shrink it a bit?

---

### Post by TheFu on 2015-08-18
I thought those settings were on the monitor/tv?
I don't have any TVs anymore, but the monitors and projectors do have those controls.

---

### Post by papibe on 2015-08-18
Hi Lee_Henderson.

From [here]("http://ubuntuforums.org/showthread.php?t=2280454&p=13340561#post13340561"), I understand it is TV you're trying to connect to?

What is the brand and model?

Also, could you open a terminal, run these commands, and post back the results (you can copy/paste the output)?
```
lspci -nnk | grep -iA2 vga
 
xrandr -q

xrandr --q1
```
Regards.

---

### Post by efflandt on 2015-08-18
Check the menus of the HDTV. Some have a setting that will work better than 16:9 that attempts to size and center whatever digital video signal it is receiving. On the 32" 1080p LG HDTV that I use as a monitor is is called "Just Scan". On a Samsung I think it is called "Fill Screen".

---

