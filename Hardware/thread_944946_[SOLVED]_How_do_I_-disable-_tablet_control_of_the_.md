---
title: "[SOLVED] How do I -disable- tablet control of the mouse?"
date: 2008-10-11
forum: Hardware
---

### Post by andrewkk on 2008-10-11
My USB ["DigiPro" UC-Logic Genius MousePen 5x4 Tablet]("http://sellout.woot.com/Forums/ViewPost.aspx?PostID=2011241") works "out of the box" as a normal mouse, but to get pressure sensitivity I had to [install the Wizardpen driver]("https://help.ubuntu.com/community/TabletSetupWizardpen"). This all worked as it should have -- except that the system is still using the tablet as a normal mouse. The result of this is a compounding effect where any movement on the tablet controls the cursor both as a normal, motion-accelerated (this is bad) mouse, and as an absolute-positioned tablet stylus.

How do I disable the "out of the box" mouse control so that all I'm using is driver I chose? What part of the system is responsible for the "out of the box" behavior?

---

### Post by andrewkk on 2008-10-11
> **andrewkk said:**
> What part of the system is responsible for the "out of the box" behavior?

[FONT="Courier New"]$ xinput test "Configured Mouse"[/FONT] logs movement from both my normal mouse and from the tablet. Does this mean that the [FONT="Courier New"]"Configured Mouse"[/FONT] stanza in xorg.conf is responsible for the "out of the box" behavior?

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection
```

Edit:
Yep. Because there was no [FONT="Courier New"]Device[/FONT] option specified, X11 had been automatically selecting all mice to use as the core pointer. (Thanks, [Zack]("http://digitalbluewave.blogspot.com/2008/04/genius-wizardpen-with-hardy-heron-and.html#c629010673549550642")) Explicitly listing the correct mouse prevented auto-detection of the tablet as a core pointer, thus disabling the "out of the box" behavior. My final xorg.conf is as follows:

```
# xorg.conf (X.Org X Window System server configuration file)

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"colemak"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
[COLOR="Red"]	Option		"Device"	"/dev/input/mouse2"[/COLOR]
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

[COLOR="Red"]Section "InputDevice"
	Identifier	"WizardPen Tablet"
	Option		"SendCoreEvents" "true" 
	Driver		"wizardpen"
	Option		"Device"	"/dev/tablet-event"
	Option		"TopX"		"2799"
	Option		"TopY"		"4259"
	Option		"BottomX"	"30756"
	Option		"BottomY"	"29521"
	Option		"MaxX"		"30756"
	Option		"MaxY"		"29521"
EndSection[/COLOR]

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
[COLOR="Red"]	InputDevice	"WizardPen Tablet"[/COLOR]
EndSection
```

---

### Post by sandos on 2008-10-25
Weird, my xorg config already looks like this, but I still get events from both my "pen" device and my "Configured Mouse".

Edit: ok, it seems its my /dev/input/mice thing which gets events from both mouse and tablet. I guess I need to use something more specific?

It was easy. In my /dev/input folder I actually 3 mice: mouse0, mouse1 and mouse2. cat:ing them gave me that my regular mouse was mouse2.

---

### Post by Arthur Millar on 2008-11-05
> **sandos said:**
> Weird, my xorg config already looks like this, but I still get events from both my "pen" device and my "Configured Mouse".

Edit: ok, it seems its my /dev/input/mice thing which gets events from both mouse and tablet. I guess I need to use something more specific?

It was easy. In my /dev/input folder I actually 3 mice: mouse0, mouse1 and mouse2. cat:ing them gave me that my regular mouse was mouse2.

my computer also shows 3 mice 
it seems the buttons for my tablet are emulated on the 
Macintosh mouse button emulation

---

### Post by Arthur Millar on 2008-11-05
.

---

### Post by nmitsis on 2012-03-13
The reason iam writing to this post is that i have a problem with my tablet and i think my mouse has to do with it.When pc boots up i can move pen without touching tablet and normally the cursor moves, BUT when i touch tablet for first time something bizare happens.I can no longer move the cursor on the screen without touching pen to tablet.Sorry for my bad english and ty for advance.:p

---

