---
title: "Touchpad and USB mouse events"
date: 2006-03-23
forum: Hardware &amp; Laptops
---

### Post by DJ Scribblinni on 2006-03-23
Hows it going everyone.  I use a laptop with both an ALPS touchpad, and I also have a USB mouse to keep it easy to do work.  I'm constantly mobile so the USB mouse is also unplugged a lot also.  The situation is I followed the guide: [http://ubuntuforums.org/showthread.php?t=78904&page=1]("http://ubuntuforums.org/showthread.php?t=78904&page=1")
to get my trackpad to work with scrolling and such, and it worked great.  The situation I have is when the computer is restarted and such, the event assignements change inbetween each mouse depending on whether the mouse USB mouse is plugged in.  So sometimes the trackpad will work, and other times, it's not.  If anyone can point me in a direction where maybe I can possible statically assign the events, or write something in the xorg for the USB mouse,or if there is another solution, please tell me.
The relevent xorg.config: ```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier 	"ALPS"
	Driver 		"synaptics"
	Option 		"AlwaysCore"
	Option 		"Device"		"/dev/input/event2"
	Option 		"Protocol"		"event"
	Option 		"LeftEdge" 		"120"
	Option 		"RightEdge" 		"830"
	Option 		"TopEdge" 		"120"
	Option 		"BottomEdge" 		"650"
	Option 		"FingerLow" 		"14"
	Option 		"FingerHigh" 		"15"
	Option 		"MaxTapTime" 		"180"
	Option 		"MaxTapMove" 		"110"
	Option 		"ClickTime" 		"0"
	Option 		"EmulateMidButtonTime" 	"75"
	Option 		"VertScrollDelta" 	"10"
	Option 		"HorizScrollDelta" 	"0"
	Option 		"MinSpeed" 		"0.45"
	Option 		"MaxSpeed" 		"0.75"
	Option 		"AccelFactor" 		"0.020"
	Option 		"EdgeMotionMinSpeed" 	"200"
	Option 		"EdgeMotionMaxSpeed" 	"200"
	Option 		"UpDownScrolling"	"1"
	Option 		"CircularScrolling" 	"0"
	Option 		"CircScrollDelta" 	"0.1"
	Option 		"CircScrollTrigger" 	"2"
	Option 		"SHMConfig" 		"true"
EndSection
```

the cat /proc/bus/input/devices output:```
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

I: Bus=0003 Vendor=046d Product=c50a Version=2010
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.0-1/input0
H: Handlers=mouse2 event4 ts2
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=103
```

---

