---
title: "touchpad no longer  working"
date: 2007-03-01
forum: Hardware &amp; Laptops
---

### Post by bubzilla on 2007-03-01
I'm running Edgy (6.10) on an HP dv4000 laptop.
The other day while attempting to mount a USB  device, Ubuntu locked up. I had to do a hard shut down to get out of it. When I restarted the touchpad wasn't working. I have a USB mouse that works fine.

The relevant parts of /etc/X11/xorg.conf (I think)
> 

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Options		"SHMConfig"		"true"	
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection



...and the output of cat /proc/bus/input/devices
> bubba@Funktastic-9000:~$ cat /proc/bus/input/devices
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0 
B: EV=120013
B: KEY=1004 2200002 3802078 f950d401 f2ffffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=045e Product=0039 Version=0121
N: Name="Microsoft Microsoft IntelliMouse&#65533; Optical"
P: Phys=usb-0000:00:1d.1-2/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0 
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103

Hope that means more to someone else.
Also, if anyone has any better suggestions about how to unlock my system or reboot without problems should this happen again, I'd be very appreciative.

Thanks, b

---

