---
title: "Touchpad &quot;tap zones&quot; for side button actions"
date: 2007-08-06
forum: Hardware &amp; Laptops
---

### Post by samosamo on 2007-08-06
I have a Compaq v2000z with a Synaptics touchpad.  In the window drivers you have what are called "tap zones" in which you can define an action when one of the 4 corners of the touchpad are "tapped."

If this is not possible, is there any other way for smooth navigation using the touchpad when using Firefox or Nautilus?

I personally had mine set up for:

left bottom - "back" button
right bottom - "forward" button
left top - n/a
right top - middle click

---

### Post by Kralizec on 2007-08-06
I'm not sure how to set up the forward and back buttons (unless you know the configuration of a 4 or 5 button mouse and which number buttons do each function). But you can set up a zone to do a middle click by adding another option to your touchpad section in your xorg.conf:

```

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	**Option      "RBCornerButton" "2"**
	Option	    "HorizScrollDelta" "0"
	Option	    "SHMConfig" "true"
EndSection

```

This will set the right-bottom corner to middle-click (supposedly, I found this in another forum). I would imagine that you could change which area does this by changing RBCorner to, say, RTCorner for right-top corner, etc. And if you knew which buttons do forward and back by default, you could probably change the number after the area name to perform that.

Alternately, there are two simple ways to simulate a middle-click without modifying your xorg.conf: hold ctrl when left-clicking and clicking both right and left buttons at the same time.

Finally, a simple tool to configure some options for your touchpad (although not your tap-zones) is qsynaptics. Install with ```
sudo apt-get install qsynaptics
``` in terminal and run by typing 'qsynaptics'.

---

### Post by samosamo on 2007-08-06
Yeah, I suppose that would work.  I follow a tutorial to set up a 5 button mouse and then define Options in Xorg.conf

Option      "LBCornerButton" "3"
Option      "RBCornerButton" "4"

From there, I wonder, can I tell Firefox that a click from the LBCornerButton means "back" ?  Maybe theres an extension I can install?  I'm doubtful because in Windows its as easy as setting in the driver that LBCornerButton means "back" for any program.

---

### Post by Kralizec on 2007-08-06
I'm sure there's a way out there, Linux developers are very crafty. Its just difficult for them to provide apps like in Microsoft because they're striving to do the opposite of M$; that is, they're trying not to assume what everyone wants.

---

### Post by ugm6hr on 2007-08-06
This gives a full manual re: configuring the touchpad in Linux (by editing xorg.conf):
```
man synaptics
```

The pre-set shortcuts in Firefox: [http://www.mozilla.org/support/firefox/keyboard#](http://www.mozilla.org/support/firefox/keyboard#)

---

### Post by samosamo on 2007-10-28
May I bump this ?

---

### Post by dougleduck on 2008-01-22
re-bump

---

### Post by EricDB on 2008-02-06
I'm working on the same problem.  I have corner zones working for right- and middle-click (not that I really want to use them for that), but I'm still trying to figure out how to map a corner click to "forward" or "back" in Firefox.  I tried mapping them to buttons "6" and "7" using synclient, but that had no effect within Firefox.

---

### Post by SZ07 on 2008-07-17
This is a very late reply but I want to add it for reference purposes.

I am using Hardy Heron with Firefox 3 and this is how I got back/forward buttons mapped to the bottom left and bottom right zones of my touchpad.

This is how my xorg.conf looks like:

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option 		"Buttons" 		"9"
	Option 		"ButtonMapping" 	"1 2 3 8 9"	
	Option 		"LTCornerButton" 	"2"
	Option 		"LBCornerButton" 	"8"
	Option 		"RBCornerButton" 	"9"
EndSection
```

Buttons option is set to 9. ButtonMapping option includes buttons 8 and 9. LBCorner is mapped to button 8 and RBCorner is mapped to button 9.

The reason the buttons have to be 8 and 9 is because 6,7 are used for horizontal scroll and 4,5 for vertical scroll. Buttons 1,2 and 3 are left, right and middle respectively. I believe FF3 automatically assumes buttons 8,9 are back/forward.

So far I've only gotten back/forward functionality in Firefox (where its most needed!). This method doesn't work for nautilus and other apps.

---

