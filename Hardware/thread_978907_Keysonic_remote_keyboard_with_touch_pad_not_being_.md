---
title: "Keysonic remote keyboard with touch pad not being recognized properly"
date: 2008-11-11
forum: Hardware
---

### Post by mrpete2004 on 2008-11-11
Hi. I've got a keysonic remote keyboard with integrated touchpad. The keyboard works fine but the touchpad is being recognized as a mouse. i.e. if I do an an xinput list I get the following:-

"Virtual core keyboard"	id=0	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Virtual core pointer"	id=1	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
"Macintosh mouse button emulation"	id=2	[XExtensionPointer]
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
"2.4G USB RF KeyBoard"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"2.4G USB RF KeyBoard"	id=4	[XExtensionPointer]
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
"2.4G USB RF KeyBoard"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255

Its usable but I would really like to map the mouse input to the synaptics driver. Is there anyway to do this? I'm using ubuntu 8.10 which does all this kind f stuff via HAL fdi policy files. How one maps a mose event to the synaptics driver I've no idea.

---

