---
title: "how to: enable &quot;clicklock&quot; for synaptics touchpad"
date: 2009-04-18
forum: Hardware
---

### Post by Choad on 2009-04-18
This wasn't trivial to find a solution to (i eventually found the option while looking through the source code of the driver) so i thought i'd make a thread about it.

clicklock is where when you drag something using the touch pad it stays grabbed until you tap again. you can drag for long distances using repeat drags this way. its like the way mac does it.

ubuntu uses hal now so if there's a way to do it via that then it would be better but i couldn't get it to work.

in your /etc/X11/xorg.conf put the following at the end

```


Section "InputDevice"
	Identifier	"SynPS/2 Synaptics TouchPad"
	Driver 		"synaptics"
	Option		"CorePointer"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"SHMConfig"	"true"
	Option		**"LockedDrags"**	"true"
EndSection

```

no guarantees so back up your xorg.conf first. if you've never done this stuff before learn how to restore a file from a backup via command line in case it goes bad.

---

### Post by alawson on 2010-04-19
Thanks very much!

This worked for me on a Asus eeePC 1000HG with eeebuntu.

---

