---
title: "[SOLVED] Synaptics Touchpad"
date: 2008-04-20
forum: Hardware &amp; Laptops
---

### Post by dwdude on 2008-04-20
I'm using Ubuntu Gutsy and I'm having an issue with my mousepad.

It just randomly functions differently.

I have it configured so that when I touch the mouse pad, it doesn't click. And I also have it so it's not really really fast.

But after a while of using it, it's WAY more sensative and the touch-click works.

System > Preferences > Mouse shows the way I had configured it before, but it doesn't function that way.

It's really obnoxious because I accidently close screens, click where I don't want to, and it's annoying to control when it's so fast.

Any ideas on how to make this stop?


xorg.conf:

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection 
 
```

Tell me if you need any other information.

Any and all help is appreciated.

Thanks!

Dave

EDIT: Found a temporary solution: If I click "Switch users", then log right back onto mine, the mouse gets fixed. It won't be long until it gets messed up again though...

---

### Post by petzworld999 on 2008-04-21
Adding 

```

Option     "MaxTapTime"   "0"


```
to your posted section of xorg.conf will fix the tapping problem. I don't know about the other erroneous stuff.

---

### Post by dwdude on 2008-04-21
Thanks, that stopped the tapping problem.

Logging out and in/resarting my computer fixes the problem. I guess I'll call this solved.

---

