---
title: "Synaptics Touchpad Scroll Region"
date: 2008-08-11
forum: Hardware
---

### Post by waspbloke on 2008-08-11
I have installed and configured ubuntu 8.04 (me n00b) on my laptop, got everything working as I would like (even got Unreal Tournament working), all except the touchpad.

Basically, how do I set the size of the scoll region?

In windows there was a GUI applet in control panel to set the scroll region size. I have added the synaptics config package in ubuntu but it is fairly minimal. The xorg.conf file only contains a few lines:

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"SHMConfig"	"on"
	Option		"HorizEdgeScroll"	"0"
EndSection
```

The problem I have is that in windows, I had the Vertical Scroll region clamped to a thin strip up the right edge, just about enough for the tip of my finger. However, in ubuntu the scroll region is set quite wide.

When I am scrolling and then I scoot my finger diagonally up to the top left for a menu action, the wider scroll region causes the page to scroll up away from the secton I was viewing.

This is annoying.

I have found this page:
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Manual_Configuration](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Manual_Configuration)
which has various settings but it is not clear to me what if anything I can do.

Grateful for any help.

**[COLOR="DarkRed"]******* EDIT: Solved! ********[/COLOR]**

Okay, I have figured it out after some playing around.

I haven't seen this problem explicitly addressed in a forum search so for anybody else who hits this post, here's the cure:

In a terminal window, type:
**man synaptics**
This will display the manual giving a list and description of all the parameters.

In a terminal window, type:
**synclient -l**
This will list all the current values of the synaptics device parameters.


To test your new scroll region settings live, type:

**synclient RightEdge=5400** (was 5072)
This shifts the right edge of the scroll region towards the right edge of the touchpad.

**synclient VertScrollDelta=100** (was 60)
This increases the amount of vertical movement that must be performed before a scroll event is registered.


When you have finished testing the parameters you wish to adjust, type:
**synclient -l**
once more to confirm your new settings.

Then type:
**sudo gedit /etc/X11/xorg.conf**
and enter your password to open up the config file for editing.

Then add the options to the InputDevice section:

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"SHMConfig"	"on"
	Option		"HorizEdgeScroll"	"0"
[B]	Option		"RightEdge"	"5400"
	Option		"VertScrollDelta"	"100"[/B]
EndSection
```

Save it, close it and restart the session.

That's it. Hope that helps anyone else who wants to tinker with the touchpad settings.

---

### Post by afeasfaerw23231233 on 2009-06-26
Thanks! It solved my problem!

---

### Post by timmyhiggy on 2009-12-15
Hi

I would love to do this but unfortunately my xorg.conf only has the following in it:

```

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

```

and synaptics isn't mentioned anywhere. What should I do to edit it?

---

### Post by timmyhiggy on 2009-12-17
mini-bump...

---

### Post by timmyhiggy on 2009-12-23
What I want to know is whether it is ok to just add something like:

> Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
        Option          "RightEdge=5900"
EndSection

To the xorg.conf I posted above.

---

### Post by sometimes on 2010-04-03
I found an answer to this here:
[http://www.bhagwad.com/blog/2009/technology/configure-alps-synaptics-touchpad-in-ubuntu-904-jaunty-jackalope.html](http://www.bhagwad.com/blog/2009/technology/configure-alps-synaptics-touchpad-in-ubuntu-904-jaunty-jackalope.html)

Worked for me to fix the width of the right-edge scroll zone in Karmic.

---

