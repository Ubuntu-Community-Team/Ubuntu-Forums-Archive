---
title: "I just want to change the working area for my Wacom"
date: 2010-03-01
forum: Hardware
---

### Post by dennus on 2010-03-01
Did a fresh install of Ubuntu 9.10. My Wacom Bamboo is working fine. The only thing a I want to change is the size of the working surface. I really hate moving my hand all around the tablet. I have no xorg.conf in  /etc/X11/ and the output of xinout --list is as follows.  Anyone care to help?

---
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Wacom Bamboo"	id=2	[XExtensionKeyboard]
	Type is Wacom Stylus
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 14760
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 9225
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 511
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Wacom Bamboo pad"	id=3	[XExtensionKeyboard]
	Type is Wacom Pad
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 4
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 14760
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 9225
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 511
		Resolution is 1
	Axis 3 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 4 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 5 :
		Min_value is 0
		Max_value is 71
		Resolution is 1
"Wacom Bamboo cursor"	id=4	[XExtensionKeyboard]
	Type is Wacom Cursor
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 14760
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 9225
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 511
		Resolution is 1
	Axis 3 :
		Min_value is -900
		Max_value is 899
		Resolution is 1
	Axis 4 :
		Min_value is -1023
		Max_value is 1023
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"NOVATEK USB Keyboard"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"NOVATEK USB Keyboard"	id=6	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Asus EeePC extra buttons"	id=7	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=8	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Wacom Bamboo eraser"	id=9	[XExtensionKeyboard]
	Type is Wacom Eraser
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 14760
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 9225
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 511
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Power Button"	id=10	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=11	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=12	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
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
"HID 04d9:1135"	id=13	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 13
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

---

