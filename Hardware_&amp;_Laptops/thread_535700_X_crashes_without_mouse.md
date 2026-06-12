---
title: "X crashes without mouse"
date: 2007-08-26
forum: Hardware &amp; Laptops
---

### Post by Tangee on 2007-08-26
I would like to apologise firstly for the vagueness this post will probably contain, as I set the laptop up a while ago and cannot remember exactly what I did, but here goes...

I am using evdev for my USB mouse on my laptop, and if I start the laptop with no mouse plugged in X crashes.

Is there a way I can tell it not to require the mouse to be plugged in but to use the touchpad if it isn't?

If you need more info please ask and I'll do my best :)

---

### Post by ankorie on 2007-08-26
hello, it sounds like your /etc/X11/xorg.conf is not configured to use your touchpad. The section you  are looking for is "InputDevice" you need a different "InputDevice" section for all of your mice/tablets/touchpads. I have a synaptics touchpad on my laptop and here is an example of what my xorg.conf looks like:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

```
You would need to set up the "Driver" line with the correct driver and the Option  "Device" with the location of your touchpad.
hope this helps
Ank

---

### Post by Tangee on 2007-08-26
My touchpad works fine as well as my USB mouse...it's just that X seeems to NEED my mouse as opposed to just be able to use it when its plugged in...

Here are the relevant sections of my xorg.conf: 

```
Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "evdev"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/event9"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection
```

could it be the corepointer line? I'm pretty sure I put that in there from the evdev guide i used to get the side buttons working on the mouse...

---

### Post by ankorie on 2007-08-26
your problem might lie with evdev here is a ubuntu bug report that might be relevant [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/97643]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/97643")
this guy found a solution for the Xorg crashing [http://www.chrisweldon.net/index.php?/archives/60-Xorg-7.1-and-evdev-problems-Solved.html]("http://www.chrisweldon.net/index.php?/archives/60-Xorg-7.1-and-evdev-problems-Solved.html")
hope this helps some,
Ank

---

### Post by ankorie on 2007-08-26
I have another idea! You can make your touchpad your "CorePointer" and then set your USB mouse to "SendCoreEvents" "true" that might just fix it. It should look something like this:

```
Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "evdev"
	#Option	    "CorePointer"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/input/event9"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	#Option	    "SendCoreEvents" "true"
	Option	    "CorePointer"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection
```

and if it does not work you can easily change it back by moving the comments around.

---

### Post by Tangee on 2007-08-27
Worked a treat! thanks!

So simple in the end...I'm kicking myself for not thinking harder... :)

---

