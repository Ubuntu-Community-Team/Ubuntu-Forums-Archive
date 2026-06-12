---
title: "Scroll Wheel emulation with Logitech Optical Trackman"
date: 2006-08-27
forum: Hardware &amp; Laptops
---

### Post by max_dingemans on 2006-08-27
So I have a Logitech Wireless Optical Trackman, and I've managed to get everything I want working to work, except one thing.

Background: I currently have button two (mousewheel button) set to emulate the mouse wheel with both horizontal and vertical scrolling, and it works fine. I also have emulate 3 button mouse on, so clicking buttons one and three (right and left click) at the same time acts as if it's the wheel button, which closes tabs in firefox,etc. That also works perfectly.

The problem: I want the emulated wheelbutton (that is, hitting one and three simultaneously) to emulate vertical and horizontal scrolling the way hitting button two does. 

What confuses me is that using xev to test events shows an identical result to hitting button 2 and the emulated button 2, both on the click and release events. xev also shows that when button two is pressed, moving the trackball shows buttons 4-7 (aka, the scrolling) being pressed as if they were real buttons. But when I try to emulate the mousewheel with buttons one and three and try to move the trackball around, xev shows events consistent with simply moving the trackball around.

And if it's helpful at all, here's the relevant Xorg.conf section:
Section "InputDevice"
	  Identifier  "Configured Mouse"
	  Driver      "mouse"
	  Option	    "CorePointer"
	  Option	    "Device" "/dev/input/mice"
	  Option	    "Protocol" "ExplorerPS/2"
	  Option	    "Buttons" "10"	
	  Option	    "ZAxisMapping" "4 5"
	  Option	    "Emulate3Buttons" "true"
	  Option      "EmulateWheel" "on"
	  Option      "EmulateWheelButton" "2"
	  Option      "Resolution" "800"
	  Option      "XAxisMapping" "6 7"
EndSection


So I guess what I'm asking for is suggestions on what else to try, or if it's even possible. 

Thanks

---

