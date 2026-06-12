---
title: "Mouse G500 logitech button map"
date: 2012-04-03
forum: Hardware
---

### Post by cazazo on 2012-04-03
Hi, I'm using Ubuntu 10.10 for a while and after I reinstall it my mouse is not functioning quite well! The G500 has 10 buttons on it and it used to work fine before reinstalling unbuntu 10.10.
It does work up to the "back" and "forward" side thumb buttons... the third one doesn't work, even though has been working under the event grab test! Any Ideas??? I think the system is using the one having the id=12 that's why is not working... but only my guess...
Please have a look at the outputs below... thank you for helping before hand!


```
~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech G500                           	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Logitech G500                           	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; UVC Camera (046d:0821)                  	id=8	[slave  keyboard (3)]
    &#8627;   USB Keyboard                          	id=9	[slave  keyboard (3)]
    &#8627;   USB Keyboard                          	id=10	[slave  keyboard (3)]


:~$ xinput get-button-map 12
1 2 3 4 5 6 7 

:~$ xinput get-button-map 11
1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 

:~$ xev | grep ', button'
    state 0x10, button 8, same_screen YES
    state 0x10, button 8, same_screen YES
    state 0x10, button 9, same_screen YES
    state 0x10, button 9, same_screen YES
    state 0x10, button 10, same_screen YES
    state 0x10, button 10, same_screen YES

:~$ xinput list-props 11
Device 'Logitech G500':
	Device Enabled (142):	1
	Coordinate Transformation Matrix (144):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (266):	0
	Device Accel Constant Deceleration (267):	1.000000
	Device Accel Adaptive Deceleration (268):	1.000000
	Device Accel Velocity Scaling (269):	10.000000
	Evdev Reopen Attempts (259):	10
	Evdev Axis Inversion (270):	0, 0
	Evdev Axes Swap (272):	0
	Axis Labels (273):	"Rel X" (152), "Rel Y" (153)
	Button Labels (274):	"Button Left" (145), "Button Middle" (146), "Button Right" (147), "Button Wheel Up" (148), "Button Wheel Down" (149), "Button Horiz Wheel Left" (150), "Button Horiz Wheel Right" (151), "Button Side" (261), "Button Extra" (262), "Button Forward" (263), "Button Back" (264), "Button Task" (265), "Button Unknown" (260), "Button Unknown" (260), "Button Unknown" (260), "Button Unknown" (260), "Button Unknown" (260), "Button Unknown" (260), "Button Unknown" (260), "Button Unknown" (260), "Button Unknown" (260), "Button Unknown" (260), "Button Unknown" (260), "Button Unknown" (260)
	Evdev Middle Button Emulation (275):	2
	Evdev Middle Button Timeout (276):	50
	Evdev Wheel Emulation (277):	0
	Evdev Wheel Emulation Axes (278):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (279):	10
	Evdev Wheel Emulation Timeout (280):	200
	Evdev Wheel Emulation Button (281):	4
	Evdev Drag Lock Buttons (282):	0


:~$ xinput list-props 12
Device 'Logitech G500':
	Device Enabled (142):	1
	Coordinate Transformation Matrix (144):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (266):	0
	Device Accel Constant Deceleration (267):	1.000000
	Device Accel Adaptive Deceleration (268):	1.000000
	Device Accel Velocity Scaling (269):	10.000000
	Evdev Reopen Attempts (259):	10
	Evdev Axis Inversion (270):	0, 0
	Evdev Axis Calibration (271):	<no items>
	Evdev Axes Swap (272):	0
	Axis Labels (273):	"Abs Volume" (284)
	Button Labels (274):	"Button 0" (283), "Button Unknown" (260), "Button Unknown" (260), "Button Wheel Up" (148), "Button Wheel Down" (149), "Button Horiz Wheel Left" (150), "Button Horiz Wheel Right" (151)
	Evdev Middle Button Emulation (275):	2
	Evdev Middle Button Timeout (276):	50
	Evdev Wheel Emulation (277):	0
	Evdev Wheel Emulation Axes (278):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (279):	10
	Evdev Wheel Emulation Timeout (280):	200
	Evdev Wheel Emulation Button (281):	4
	Evdev Drag Lock Buttons (282):	0


```

---

