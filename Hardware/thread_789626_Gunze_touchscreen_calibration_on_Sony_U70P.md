---
title: "Gunze touchscreen calibration on Sony U70P"
date: 2008-05-10
forum: Hardware
---

### Post by geoque on 2008-05-10
Hello,

I have just installed Ubuntu 8.04 on my Sony u70p ultra-mobile PC.  So far everything seems to be going well except for the touchscreen.  I have found some info about evtouch drivers, but wanted some advice before investing too much time in changing things around. Here is my specific experience:

The arrow moves around the screen in the general direction of the location that I press, but there is no precision at all.  The cursor moves in odd directions at somewhat erratic speeds.  I have used the **cat /proc/bus/input/devices** command and came up with this output:

I: Bus=0003 Vendor=0637 Product=0003 Version=0110
N: Name="GUNZE USB Touch Panel"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input7
U: Uniq=
H: Handlers=mouse2 event7 js0 
B: EV=1b
B: KEY=70000 0 0 0 0 0 0 0 0
B: ABS=3
B: MSC=10

After performing this operation, I then opened the xorg.conf file:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection


So, I guess my main question is;  Do I need to change anything in the xorg.conf, or (since I already have limited touchscreen functionallity) can I just somehow calibrate it?  If calibration is possible, what utility can I use?  If it requires modification of the .conf files, however, can anyone suggest how I might go about this?  I am quite new to linux, so your patience is greatly appreciated.  Also, I am not quite sure which of the "InputDevice" entries relates to the Gunze touchscreen.  Does anyone have any insight into this as well.

Thanks much,
Geoque

---

