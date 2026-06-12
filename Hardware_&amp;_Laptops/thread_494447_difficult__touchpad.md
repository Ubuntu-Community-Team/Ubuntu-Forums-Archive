---
title: "difficult  touchpad"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by Darkcloud on 2007-07-06
Hi  just wondering if anyone else has this problem or if there is a way I can fix it.  Seems that the touchpad using Ubuntu is much more difficult than on a windows os. Its getting a bit annoying,  such as  if I move the cursor the page is moving and I have to tap rather strongly to get it to stop  I have had windows on the same laptop and this doesn't happen. Any ideas as to the cause?

---

### Post by kerry_s on 2007-07-06
okay, i'll throw a idea out, "setup your touch pad"

[http://linuxinside.blogspot.com/2007/06/touchpad-configure-it.html](http://linuxinside.blogspot.com/2007/06/touchpad-configure-it.html)

---

### Post by Darkcloud on 2007-07-07
Thank you  and I went there and  for some reason (probably me) I don't have a xorg.conf file. When I ask for it thru termminal  its a blank page  nothing there    I am sure this tutorial you sent is good  but now i need to know why I don't have this configuration file anywhere

---

### Post by Darkcloud on 2007-07-07
yeah ok nevermind it was me   duh   sorry   my touchpad is behaving better now

---

### Post by strabes on 2007-07-07
Here's the relevant section of my /etc/X11/xorg.conf:

> 
Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "SHMConfig" "true"
	Option	    "MinSpeed" ".1"
	Option	    "MaxSpeed" ".3"
	Option	    "AccelFactor" ".0017"
	Option	    "MaxTapTime" "150"
	Option	    "MaxDoubleTapTime" "150"
	Option	    "VertEdgeScroll" "1"
	Option	    "HorizEdgeScroll" "1"
	Option	    "VertScrollDelta" "300"
	Option	    "HorizScrollDelta" "250"
	Option	    "BottomEdge" "4300"
	Option	    "RightEdge" "5250"
	Option	    "TapButton2" "2"
	Option	    "TapButton3" "3"
	Option	    "RTCornerButton" "0"
	Option	    "RBCornerButton" "0"
	Option	    "LTCornerButton" "0"
	Option	    "LBCornerButton" "0"
EndSection

I have a dell inspiron E1705.

---

