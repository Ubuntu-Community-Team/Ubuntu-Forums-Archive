---
title: "alps touchpad and reboot"
date: 2005-10-24
forum: Hardware &amp; Laptops
---

### Post by fgosse on 2005-10-24
Hi 
I have a laptop inspiron 6000 with Breezy.
I 've modified /etc/X11/xorg.conf to use the touchpad (scrollbars, drag and..)
Now it works properly : Great !!!

But when i reboot, the modifications don't working. I must restart gdm (/etc/init.d/gdm restart) to use the touchpad with all fonctionnality.

Why ???
Thanks a lot and sorry if my english is not very well

F.G

---

### Post by chris86wm on 2005-11-08
Hey man, sry i cant help you but would you mind posting what you did to get your touchpad working temporarily. i have the same laptop as you do and i would love to get this fixed. thanks

---

### Post by GoodPanos on 2005-11-08
Hello!

I have the same notebook and I got mine working.
First you have to make sure you have the latest and greatest of Breezy (not release preview).
Then follow **Scubajeff's** instructions from this link [http://ubuntuforums.org/showthread.php?t=78904](http://ubuntuforums.org/showthread.php?t=78904)
Also add this line too to your xorg.conf file: *Option "GuestMouseOff" "0"*.

Your touchpad should work right off the back.

If you notice from my posts I had a lot of issues.  I was using 5.10 the preview release.  So I did a clean install and then followed the above mentioned instructions and it worked great.

---

### Post by fgosse on 2005-11-08
Thanks a lot.
My touchpad works now perfectly after a reboot.

F.G

---

### Post by chris86wm on 2005-11-09
hmm i cant seem to get it to work
here is what i get after the command :
** cat /proc/bus/input/devices**

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=1 80000004 2000000 3002078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="PS/2 Mouse"
P: Phys=isa0060/serio1/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse1 event2 ts1
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
H: Handlers=kbd event3
B: EV=40001
B: SND=6
[B]
also here is my xorg.conf
[/B]
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
Identifier "ALPS"
Driver "synaptics"
Option "AlwaysCore"
Option "Device" "/dev/input/event2"
Option "Protocol" "event"
Option "LeftEdge" "120"
Option "RightEdge" "830"
Option "TopEdge" "120"
Option "BottomEdge" "650"
Option "FingerLow" "14"
Option "FingerHigh" "15"
Option "MaxTapTime" "180"
Option "MaxTapMove" "110"
Option "ClickTime" "0"
Option "EmulateMidButtonTime" "75"
Option "VertScrollDelta" "10"
Option "HorizScrollDelta" "0"
Option "MinSpeed" "0.45"
Option "MaxSpeed" "0.75"
Option "AccelFactor" "0.020"
Option "EdgeMotionMinSpeed" "200"
Option "EdgeMotionMaxSpeed" "200"
Option "UpDownScrolling" "1"
Option "CircularScrolling" "0"
Option "CircScrollDelta" "0.1"
Option "CircScrollTrigger" "2"
Option "SHMConfig" "true"
Option "GuestMouseOff" "0"
EndSection

am i doing something wrong?

---

### Post by fgosse on 2005-11-09
perhaps...
You have two touchpads in your /etc/X11/xorg.conf. 
Try to delete :

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

and keep :

Section "InputDevice"
Identifier "ALPS"
Driver "synaptics"
Option "AlwaysCore"
Option "Device" "/dev/input/event2"
Option "Protocol" "event"
Option "LeftEdge" "120"
Option "RightEdge" "830"
Option "TopEdge" "120"
Option "BottomEdge" "650"
Option "FingerLow" "14"
Option "FingerHigh" "15"
Option "MaxTapTime" "180"
Option "MaxTapMove" "110"
Option "ClickTime" "0"
Option "EmulateMidButtonTime" "75"
Option "VertScrollDelta" "10"
Option "HorizScrollDelta" "0"
Option "MinSpeed" "0.45"
Option "MaxSpeed" "0.75"
Option "AccelFactor" "0.020"
Option "EdgeMotionMinSpeed" "200"
Option "EdgeMotionMaxSpeed" "200"
Option "UpDownScrolling" "1"
Option "CircularScrolling" "0"
Option "CircScrollDelta" "0.1"
Option "CircScrollTrigger" "2"
Option "SHMConfig" "true"
Option "GuestMouseOff" "0"
EndSection


Don't forget to save your xorg.conf, if this is wrong

F.G

---

### Post by chris86wm on 2005-11-09
i just tried that and it wouldnt let ubuntu boot up until i set it back to the way it was.  any other suggestions?

---

### Post by fgosse on 2005-11-10
Humm,

My xorg.conf is :

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/event2"
        Option          "Protocol"              "event"
	Option 		"AlwaysCore"
	Option 		"LeftEdge" "120"
	Option 		"RightEdge" "830"
	Option 		"TopEdge" "120"
	Option 		"BottomEdge" "650"
	Option 		"FingerLow" "14"
	Option 		"FingerHigh" "15"
	Option 		"MaxTapTime" "180"
	Option 		"MaxTapMove" "110"
	Option 		"ClickTime" "0"
	Option 		"EmulateMidButtonTime" "75"
	Option 		"VertScrollDelta" "20"
	Option 		"HorizScrollDelta" "20"
	Option 		"MinSpeed" "0.3"
	Option 		"MaxSpeed" "0.75"
	Option 		"AccelFactor" "0.015"
	Option 		"EdgeMotionMinSpeed" "200"
	Option 		"EdgeMotionMaxSpeed" "200"
	Option 		"UpDownScrolling" "1"
	Option 		"CircularScrolling" "1"
	Option 		"CircScrollDelta" "0.1"
	Option 		"CircScrollTrigger" "2"
	Option 		"SHMConfig" "on"
EndSection

(....)

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad" "Corepointer"
EndSection "Corepointer"
EndSection

In ServerLayout is there the same name for the touchpad ?
Here is
-  Identifier      "Synaptics Touchpad"
- InputDevice	"Synaptics Touchpad"


F.G

---

### Post by GoodPanos on 2005-11-10
**chris86wm**, did you backup the original xorg.conf file?  If you did, I suggest you start all over with the original and just add the additional entries into the "Synaptics" section.

If this doesn't work for you, I can upload my xorg.conf file and you can compare the two.

---

