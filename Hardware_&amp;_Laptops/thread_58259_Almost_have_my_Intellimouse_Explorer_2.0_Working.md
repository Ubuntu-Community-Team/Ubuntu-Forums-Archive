---
title: "Almost have my Intellimouse Explorer 2.0 Working"
date: 2005-08-19
forum: Hardware &amp; Laptops
---

### Post by EnderTheThird on 2005-08-19
I've looked through just about every mouse button tutorial/HOWTO on here and through Google and I just can't find anything that works.  Here's my xorg.conf:
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Buttons"		"7"
	Option		"ZAxisMapping"		"6 7"
EndSection
```
If I change "ZaxisMapping" to "4 5" then my wheel works as backward/forward but not as scroll.  When I run "xev" in a terminal, it shows my back and forward buttons as 2 and 3, so I'm wondering if it just thinks I have a different mouse.  No matter what I do with "Buttons" or "ZAxisMapping", those buttons still don't show up as uniqe ones (as opposed to duplicates of my wheel click, 2, and right mouse, 3).  Can you guys think of anything I can do to fix this?  I don't want to mess around too much with the settings myself and wind up with a mouse that doesn't work at all.  

Oh, and if someone knows a way to get the side tilt options for the wheel working as well, that would be great.  That's not really a priority though, because I never really even used that in Windows.

---

### Post by EnderTheThird on 2005-08-19
I hate to be a pain, but does anyone have some suggestions for me?  I'd really like to get my mouse working correctly tonight, because then I'll have all of my hardware working correctly so I can try and get WoW running.  Thanks again.

---

### Post by brainkilla on 2005-08-19
Section "InputDevice"
        Identifier  "PS/2 Mouse"
        Driver      "mouse"
        Option     "Protocol" "IMPS/2"
        Option     "ZAxisMapping"          "4 5"

My xorg.conf... I'm running Sid and have Logitech Premium Optical 3-button mouse though...

---

### Post by EnderTheThird on 2005-08-19
Thanks.  I'm not sure how much that will help, but maybe I'll try changing the identifier when I get home tonight (I'm at work for another 2.5 hours).  Any other suggestions?

---

### Post by EnderTheThird on 2005-08-20
Somehow I ruined my GDE while trying to fix this, so I just re-installed.  I was able to get it to work this time following one of the tutorials.  I think changing the protocol to "ExplorerPS/2" is what did the trick though.

---

### Post by Cobra78 on 2005-08-20
[QUOTE=EnderTheThird]Somehow I ruined my GDE while trying to fix this, so I just re-installed.  I was able to get it to work this time following one of the tutorials.  I think changing the protocol to "ExplorerPS/2" is what did the trick though.[/QUOTE]
 As Ender says, try to change the protocol.

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "4 5"
EndSection

```

I have Intelli Mouse Explore and Trackball Explorer connected at the same time with usb, and with the section of xorg.conf posted above, they are working great :)

---

