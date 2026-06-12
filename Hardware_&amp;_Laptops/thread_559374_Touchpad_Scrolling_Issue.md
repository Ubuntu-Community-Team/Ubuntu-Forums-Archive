---
title: "Touchpad Scrolling Issue"
date: 2007-09-25
forum: Hardware &amp; Laptops
---

### Post by CrazyBoyD on 2007-09-25
I just set up a Gateway ML3109 with Fiesty 7.04 and everything is working perfectly, but for one minor issue with the touchpad.  On the left of the touchpad, there is a section that controls scrolling.  However, part of the adjacent touchpad is also performing the scroll function rather than the mouse pointer function like it should.  Is there any way that I can adjust which part of the touchpad scrolls and which part controls the pointer?

---

### Post by asforme on 2007-10-05
I am having the same issue on a Gateway MT6821 running Gutsy beta.

---

### Post by nick_h on 2007-10-05
Look in your xorg.conf file for a section with *Driver "synaptics"* in it.  You can add extra options in that section.

Look in the manual page for synaptics for more information:
```
man synaptics
```

I seem to remember there is also a GUI utility to configure this but I can't remember what it is.

---

### Post by asforme on 2007-10-05
Okay I've got it.

```
sudo gedit /etc/X11/xorg.conf
```

Find the section that starts with:
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
```
Add an option like the following:
```
	Option          "RightEdge"     	"5800"
```
5800 turned out to be the magic number for me, and if you have the same gateway touchpad it is likely the same for you too.  The higher the number the closer to the right edge, the lower the closer to the left edge.

My final Synaptic section looks like the following
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
        Option 		"SHMConfig"             "True"
	Option          "RightEdge"     	"5800"
EndSection
```

You will have to save the file and restart the X-server(ctrl+alt+backspace) to apply the changes.

---

### Post by Linicks on 2007-10-05
Also, have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=469639](http://ubuntuforums.org/showthread.php?t=469639)

This really helped me set up the touchpad perfectly.

Nick

---

### Post by BinaryMadman on 2007-10-05
All this was done using the method asforme mentioned.

I had the same problem as the original poster but my touchpad has the "scroll section" on the right side of the touchpad as opposed to the left side.  In my case I set the 'RightEdge' to 5890 to get it working properly.  I used the command 'synclient -m 1' to monitor where the scrollbar "bump" on the trackpad is located and gave it a nice round number of 5890. 

In your case, you might have to do the same but with the 'LeftEdge' option instead (i'm totally guessing here though).  If you see the x value stop changing while using synclient when you go over the "bump", you've gone too far.  Use the closest number you can spot before that.

---

### Post by nick_h on 2007-10-05
Yes, qsynaptics, that was the one I couldn't remember.  It should make it easier than the looking at the maunal page and editing the config as I suggested earlier.

---

