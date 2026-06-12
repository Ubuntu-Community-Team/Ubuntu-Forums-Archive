---
title: "Synaptics Touchpad: Bottom Scroll"
date: 2006-10-05
forum: Hardware &amp; Laptops
---

### Post by tonyr1988 on 2006-10-05
I've got my Synaptics Touchpad working perfectly on my laptop (as per the wiki). There is one small problem, though: while in Firefox, if I scroll along the bottom of the touchpad (like vertical scrolling, but horizontally :)), it moves back and forward through my pages. It can be a real pain, and I've made a bunch of mistakes through it. Can anyone help?

Here's the relevant snippet from my xorg.conf:

> Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
	Option	    "LeftEdge" "1700"
	Option	    "RightEdge" "4800"
	Option	    "TopEdge" "2000"
	Option	    "BottomEdge" "4100"
	Option	    "FingerLow" "25"
	Option	    "FingerHigh" "30"
	Option	    "MaxTapTime" "180"
	Option	    "MaxTapMove" "220"
	Option	    "VertScrollDelta" "100"
	Option	    "MinSpeed" "0.09"
	Option	    "MaxSpeed" "0.18"
	Option	    "AccelFactor" "0.0015"
EndSection

Can I just change BottomEdge or something?

Oh yeah, and I'm using Bon Echo Beta 2. Will soon be upgrading to 2.0rc1, if Firefox is the problem.

---

