---
title: "SHMConfig &amp; the phantom touchpad"
date: 2009-03-27
forum: Hardware
---

### Post by Citizen Bleys on 2009-03-27
I've installed Ubuntu on two separate laptops, both Dell XPS M1530s shipped with Vista.  The one I use at work functions perfectly out of the box; I was able to disable the touchpad on it through system/preferences/mouse.

My home laptop, which I also use with an external mouse or not at all, was purchased about a year later, with completely different hardware.  I think "M1530" means "This laptop has a case that says M1530 on it, nothing more."  After install, there is no touchpad tab in the mouse dialog.  Whether or not I have an external mouse connected, the touchpad does not work at all--i.e, I swirl my finger around on the touchpad for 15-30 seconds, and then the pointer will move, but not in the same direction or half the time even on the same axis as my finger.  Of course, the touchpad likes to randomly select and delete large blocks of text while I'm typing.  Love that.  In terminal windows, it likes to take a random key that I've pressed, and repeat it infinitely.  I once watched it stream the letter "s" across my screen for about 30 seconds while my hands were off of the keyboard and mouse.  Did you know that "sudo apt-get install ssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssss" is not a valid command?  Now you do.

Of course I googled for an answer.  Oh, how I googled.  And every solution has one thing in common--something called "SHMConfig" has to be enabled to do anything at all.

Here's the relevant section of my xorg.conf:

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option          "SHMConfig"             "on"
	Option		"TouchpadOff"		"1"
EndSection

```

Everything except the last 2 Options were added by Ubuntu during install.  I also tried "SHMConfig" "true".  Same results.  The touchpad still randomly buggers up everything I try to do.

I tried installing gsynaptics, and got the Touchpad applet in my System/Preferences menu.  Here's what it says:

[quote=gsynaptics]
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics[/quote]

And of course, there is no option in the BIOS to disable the touchpad.

Any ideas that don't involve fire?

EDIT:  yes I rebooted

EDIT 2:

**This issue has been resolved**

I updated to Intrepid Ibex and everything started working the way it should be.  Both the original Hardy install and the current Intrepid install are the 32-bit versions, albeit on a 64-bit processor.  I will continue running Hardy on my desktop in case of unforseen issues.

---

