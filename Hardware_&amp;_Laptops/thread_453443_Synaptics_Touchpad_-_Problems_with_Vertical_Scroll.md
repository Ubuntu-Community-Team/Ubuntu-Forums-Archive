---
title: "Synaptics Touchpad - Problems with Vertical Scroller?"
date: 2007-05-24
forum: Hardware &amp; Laptops
---

### Post by wastedfluid on 2007-05-24
I installed GSynaptics last nigh.. why, I don't know.  I just installed a fresh 32-bit copy of Ubuntu.  I installed GSynaptics,  and set Touchpadoff to 2, and MaxTapeTime to 0, with a few other options.  However, after a reboot.. my vertical scroller does NOT work.

Here are my settings..

[I]Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"Touchpadoff"		"2"
	Option		"MaxTapTime"		"0"
	Option 		"MaxTapMove"		"0"
	Option		"LeftEdge"		"1700"
	Option		"RightEdge"		"5300"
	Option		"TopEdge"		"1700"
	Option		"BottomEdge"		"4200"
	Option		"FingerLow"		"25"
	Option		"FingerHigh"		"30"
	Option		"HorizScrollDelta"	"0"
	Option		"VertScrollDelta"	"100"
EndSection[/I]

---

### Post by jbernardo on 2007-05-24
Check this thread - [http://ubuntuforums.org/showthread.php?t=417492](http://ubuntuforums.org/showthread.php?t=417492) - lots of us are having problems with touchpads.

---

### Post by steevols on 2007-05-24
I'd disable GSynaptics... I installed it myself a few weeks back, but it proved to be more trouble than it was worth. Ubuntu has touchpad settings built in. That's just my opinion, of course.

---

### Post by wastedfluid on 2007-05-24
> **jbernardo said:**
> Check this thread - [http://ubuntuforums.org/showthread.php?t=417492](http://ubuntuforums.org/showthread.php?t=417492) - lots of us are having problems with touchpads.

I thought that the ALPS was different than the Syanptics touchpad?  

What's strange is, my vertical scroller worked on the 64-bit edition. 


> 
I'd disable GSynaptics... I installed it myself a few weeks back, but it proved to be more trouble than it was worth. Ubuntu has touchpad settings built in. That's just my opinion, of course.


I'm thinking about uninstalling the entire package.  I didn't know until I started playing that modifying xorg.conf file... worked on its own.  I thought you needed the gsynaptics package for those modified settings to work.

But,

Anywho, does anyone know what I'm doing wrong?  I have the Synaptics touchpad.. and my vertical scroller isn't working.  It worked on 64-bit Ubuntu..

Thanks guys!!

---

### Post by IntuitiveNipple on 2007-05-24
I've installed GSynaptics with Feisty and an Alps touchpad and it works perfectly.

I did notice occasionally that the configuration dialog would arbitrarily change values of sliders when flicking between tabs, but as long as I reset the slider setting before closing the dialog it worked fine.

I'm really enjoying having horizontal and vertical sliders although it's taking some practice to avoid causing back/foward in the browser when accidentally catching the horizontal scroll zone!

I seem to have a lot less settings than you in /etc/X11/xorg.conf although I've certainly customised it alot:
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMconfig"	"true"
EndSection
```

---

### Post by wastedfluid on 2007-05-24
> **IntuitiveNipple said:**
> I've installed GSynaptics with Feisty and an Alps touchpad and it works perfectly.

I did notice occasionally that the configuration dialog would arbitrarily change values of sliders when flicking between tabs, but as long as I reset the slider setting before closing the dialog it worked fine.

I'm really enjoying having horizontal and vertical sliders although it's taking some practice to avoid causing back/foward in the browser when accidentally catching the horizontal scroll zone!

I seem to have a lot less settings than you in /etc/X11/xorg.conf although I've certainly customised it alot:
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMconfig"	"true"
EndSection
```



Well.  I have fixed it.

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"Touchpadoff"		"2"
	Option		"MaxTapTime"		"0"
	Option 		"MaxTapMove"		"0"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMconfig"		"true"
EndSection

```

I removed a lot of that crap, like your config.  I then actually launched gsynaptics, changed t settings - logged out, ctrl+alt+backspace... and my scrollbar works again.  And it worked.  I just wanted to paste this so anyone having the same problem with Synaptics.. hopefully they can fix it.

---

