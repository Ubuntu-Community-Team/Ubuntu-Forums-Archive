---
title: "Leftclick touchpad and mouse not working"
date: 2009-06-16
forum: Hardware
---

### Post by TrineH on 2009-06-16
I really need some help. After upgrading to Ubuntu 9.04 on my AspireOne both my mouse and touchpad are not able to left click.  

Below is some information I have gathered.  To me it seems like the problem is that the Touchpads first button has gotten the initial value as down and that this inhibit any leftclick action.  I think what needs to be done is to reset this value, but I can not find out how to do it. Some 20 years ago I did a lot of programming, but I have no experiences with Linux, so please, can anyone give me a hint on what to do, is there a command which can do it, or is it possible to find the actual memory address and write to it?

$ xinput query-state "SynPS/2 Synaptics TouchPad"
2 classes :
ButtonClass
	button[1]=down
	button[2]=up    
etc up to the last button:
	button[12]=up
ValuatorClass Mode=Relative Proximity=In
	valuator[0]=4738
	valuator[1]=4426

$ xinput query-state "A4Tech PS/2+USB Mouse" 
return all buttons as up.

$ xinput list
"SynPS/2 Synaptics TouchPad" 	id=5   [XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 1472
		Max_value is 5472
		Resolution is 1
	Axis 1 :
		Min_value is 1408
		Max_value is 4448
		Resolution is 1

"A4Tech PS/2+USB Mouse" 	id=6   [XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1

When testing what is actually happening when I press the buttons I get this result:
$ xev |grep button 
(Touchpad left no action at all)
(Touchpad right (down + up))
state 0x100, button 3, same-screen YES
state 0x500, button 3, same-screen YES
(Mouse left no action)
(Mouse right (down + up))
state 0x100, button 3, same-screen YES
state 0x500, button 3, same-screen YES
(Mouse left + right (down + up))
state 0x100, button 3, same-screen YES
state 0x300, button 3, same-screen YES
(mouse scrool down)
state 0x100, button 4, same-screen YES
state 0x900, button 4, same-screen YES
(mouse scrool up)
state 0x100, button 5, same-screen YES
state 0x1100, button 5, same-screen YES
(mouse 2x no action at all)

This is some additional information:
$ synclient -V
0.99.3

$ xinput get-button-map  "A4Tech PS/2+USB Mouse" 
1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 10

$ xinput get-button-map "SynPS/2 Synaptics TouchPad" 
1 2 3 4 5 6 7 8 9 10 11 12

$ xinput list-props "A4Tech PS/2+USB Mouse" 
Device 'A4Tech PS/2+USB Mouse':
	Device Enabled (109):			1
	Evdev Axis Inversion (246):			0, 0
	Evdev Reopen Attempts (243):		10
	Evdev Axis Calibration (244):
	Evdev Axis Swamp (245):			0
	Evdev Middel Button Emulation (247):	2
	Evdev Middel Button Timeout (248):	0
	Evdev Wheel Emulation (249):		2
	Evdev Wheel Emulation Axes (250):		0, 0, 4, 5
	Evdev Wheel Emulation Inertia (251):	10
	Evdev Wheel Emulation Timeout (252)	200:
	Evdev Wheel Emulation Button (253):	4
	Evdev Drag Lock Buttons (254)		0

---

