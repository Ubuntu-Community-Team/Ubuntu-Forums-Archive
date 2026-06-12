---
title: "scroll button configuration on fujitsu laptop"
date: 2006-08-01
forum: Hardware &amp; Laptops
---

### Post by areté on 2006-08-01
Hi folks,

First post here, so I would like to take the opportunity to thank the Ubuntu team for putting together such an awesome distribution. I managed to install ubuntu on my Fujitsu T3010D tablet pc and I am amazed by the amount of functionality that just worked.

I have one last hurdle though: the middle scroll button under the touchpad. It is supposed to work as a scroll wheel (even though it is not a wheel :) ) - clicking on its upper part to scroll up, on its lower part to scroll down.

I have searched for a way to do this but no luck so far. I have tried a few combinations of values on my xorg.conf file, which I quote below. Some material out there indicated that this might not work with the synaptics driver, and that I should try an alternate alps driver, but I was not able to go anywhere from there.

The best I could do was manage to make the lower part of the button to work as a third button by setting "Emulate3Buttons" to true. I would really like to make this behave like a scroll wheel. Can anyone point me in the right direction?

Thank you!

-----------------------------------------------------------------------
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option 		"Buttons" 		"5"
	Option		"Emulate3Buttons"	"false"
#   	Option		"EmulateWheel" 	"true"
#   	Option 		"EmulateWheelButton"	"2"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
        Option          "SHMConfig"             "on"
EndSection

---

### Post by bluetoad on 2006-08-01
Try to move your finger up and down on the extreme right hand side of the touch pad.  I tried to configure
scrolling on my Toshiba Portege M500 and found I didn't need to...

---

### Post by areté on 2006-08-01
No luck on my laptop... thank you for the tip though.

---

### Post by Fully216 on 2006-09-08
I would be interested to find out if anyone has gotten the scroll wheel on an alps touchpad to work.  I installed the synaptics thouchpad driver, which drastically improved the performance of the touchpad.  It works beautiful now, excpet for the vertical scroll wheel.  Right now it is treated as if it is just a continuation of the regular touchpad.  If I move up or down, it does not scroll but rather simply moves the mouse up and down.  This seems like a common problem, either it works or it doesn't, as I have already read a few posts on the subject.

For example,
[http://www.ubuntuforums.org/showthread.php?t=125479](http://www.ubuntuforums.org/showthread.php?t=125479)

aside from the posts I have responded to recommending the synaptics driver.  I also found no solution on the compaq r3000 wiki (because that is what I am using).

I have listed the relevant portions of my xorg.conf file below.  It is a bit complicated because I occationally use a USB Kinsington mouse.  Any help is greatly appreciated.

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"		"CorePointer"
#    InputDevice    "stylus" "SendCoreEvents"
#    InputDevice    "cursor" "SendCoreEvents"
#    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"		"AlwaysCore"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    #Option         "SendCoreEvents"		"true"
    Option	   "Device"			"/dev/psaux"
    #Option         "Device"			"/dev/input/event3"
    Option	   "Protocol"			"auto-dev"
    #Option         "Protocol" 			"event"
    Option         "LeftEdge" 			"1700"
    Option         "RightEdge" 			"5300"
    Option         "TopEdge" 			"1700"
    Option         "BottomEdge" 		"4200"
    Option         "FingerLow" 			"25"
    Option         "FingerHigh" 		"30"
    Option         "MaxTapTime" 		"0"
    Option         "MaxTapMove" 		"110"
    Option	   "ClickTime" 		        "0"
    Option         "EmulateMidButtonTime"	"75"
    Option         "VertScrollDelta"		"50"
    Option         "HorizScrollDelta"		"10"
    Option         "MinSpeed"			"0.4"
    Option         "MaxSpeed"			"1.0"
    Option         "AccelFactor"		"0.03"
    Option         "EdgeMotionMinSpeed"		"200"
    Option	   "EdgeMotionMaxSpeed"		"200"
    Option         "UpDownScrolling"		"1"
    Option	   "CircularScrolling"		"0"
    Option	   "CircScrollDelta"		"0.1"
    Option	   "CircScrollTrigger"		"2"
    Option	   "SHMConfig"			"true"
    Option         "TouchpadOff"		"0"
    #Option	   "Repeater"			"/dev/ps2mouse"
EndSection

---

