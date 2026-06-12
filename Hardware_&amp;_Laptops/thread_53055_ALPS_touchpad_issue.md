---
title: "ALPS touchpad issue"
date: 2005-07-30
forum: Hardware &amp; Laptops
---

### Post by Ben the Penguin on 2005-07-30
Hi everybody, I've just installed Ubuntu on my older Toshiba Satellite and everything works great except the touchpad.

Originally the system detected it as a PS/2 mouse and it worked fine but without the nice synaptic features, so I followed the [Ubuntu Alps How-to](http://ubuntuforums.org/archive/index.php/t-28132.html) and patched my kernel to include Alps support and it identified it. 

[SIZE=1]
[I]$sudo cat /proc/bus/input/devices
I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="AlpsPS/2 ALPS TouchPad"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse0 event1 ts0
B: EV=f
B: KEY=420 30000 670000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003[/I][/SIZE]

But now the touchpad didn't function at all in Gnome since it's input wasn't going to /dev/input/mice (where a default mouse was set up) but the Synaptic driver wasn't giving me any errors in xorg.0.log and it seemed to be detecting it just fine. If I went

[size=1]*sudo cat /dev/input/mice* or /dev/psaux or /dev/input/mouse0 or /dev/input/event1[/size] I wouldn't get anything from the touchpad.

Apparently this had something to do with USB modules and psmouse loading in weird orders, so I would rmmod and modprobe psmouse, and all of a sudden I could see input from the touchpad in cat and when I restarted X the touchpad would work (like a PS2 mouse) but now Synaptics isn't detecting the mouse and is giving me errors:
[size=1][i]
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"[/i][/size]

I'm not sure how to fix what order these modules load in (or even what order they should load in) and I don't even know if that would fix the problem or not. 

Any help would be appreciated.  I'm REALLY enjoying using Ubuntu. :D

Here's my mouse section of my xorg.conf:
[size=1][I]Section "InputDevice"
  Driver  	"synaptics"
  Identifier  	"Synaptics Touchpad"
  Option	"Device"  		"/dev/input/mouse0"
  Option	"Protocol"		"auto-dev"
  Option	"LeftEdge"		"120"
  Option	"RightEdge"		"830"
  Option	"TopEdge"		"120"
  Option	"BottomEdge"		"650"
  Option	"FingerLow"		"14"
  Option	"FingerHigh"		"15"
  Option	"MaxTapTime"		"180"
  Option	"MaxTapMove"		"110"
  Option	"EmulateMidButtonTime"	"75"
  Option	"VertScrollDelta"	"20"
  Option	"HorizScrollDelta"	"20"
  Option	"MinSpeed"		"0.2"
  Option	"MaxSpeed"		"0.5"
  Option	"AccelFactor"		"0.01"
  Option	"EdgeMotionMinSpeed"	"15"
  Option	"EdgeMotionMaxSpeed"	"15"
  Option	"UpDownScrolling"	"1"
  Option	"CircularScrolling"	"1"
  Option	"CircScrollDelta"	"0.1"
  Option	"CircScrollTrigger"	"2"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
[/I][/size]

---

### Post by Ben the Penguin on 2005-07-31
*bump*

---

### Post by c0rderr0y on 2005-07-31
have you tried checking out [http://www.linux-laptop.net/](http://www.linux-laptop.net/) ? they have a weath of information on this kind of stuff, I know they have the information on my laptop for the touchpad.

---

### Post by Ben the Penguin on 2005-07-31
Doesn't say anything special about my laptop, but thanks for the link.  The thing is I know the driver should work because I've had the touchpad working on other distros... if I use the Kanotix LiveCD is works without any configuring at all for instance.

---

### Post by Ben the Penguin on 2005-08-07
*bump*

---

### Post by mlord on 2005-08-10
[QUOTE=Ben the Penguin]*bump*[/QUOTE]
 Sounds like it needs the same kernel patch and fixes as I did for the ALPS touchpad on my Dell i9300.

[http://rtr.ca/dell_i9300/](http://rtr.ca/dell_i9300/)

---

