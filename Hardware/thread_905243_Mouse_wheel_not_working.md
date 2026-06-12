---
title: "Mouse wheel not working"
date: 2008-08-30
forum: Hardware
---

### Post by Jerry_D on 2008-08-30
Running Ubuntu 8.04 in a Microsoft VM (Virtual PC 2007) under Vista Ultimate 32-bit. Computer DELL Dimension 9200 (Intel Core 2 Duo 2.4 GHz, 4GB RAM).

I have tried several different mice and one trackball (all USB) and in neither case can I get the wheel scrolling. I did, as advised in a number of places, change the mapping with adding Option "ZAxisMapping" "4 5" in my xorg.conf, but that didn't help. Also tried evdev drivers - no avail.

Current mouse: Logitech Trackball Optical

Current xorg definition:

> Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "vmmouse"
	Option "CorePointer"
	Option "Device" "/dev/input/mice"
	Option "Protocol" "ImPS/2"
	Option "Buttons" "5"
	Option "ZAxisMapping" "4 5"
EndSection

Output from  cat /proc/bus/input/devices:

>  
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/virtual/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=000a Version=0000
N: Name="TPPS/2 IBM TrackPoint"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input4
U: Uniq=
H: Handlers=mouse1 event4 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3


How to get the wheel functionality? Anyone, please?

---

### Post by latev on 2008-10-27
Just struggling with the same issue here, except on a real installation not a VM one. Have you been able to make any progress since your last post? Please share the knowledge

---

### Post by Jerry_D on 2008-10-27
Unfortunately, no progress. :-(
Have tried a good many things, but no luck.

---

