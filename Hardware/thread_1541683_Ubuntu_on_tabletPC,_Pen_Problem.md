---
title: "Ubuntu on tabletPC, Pen Problem"
date: 2010-07-29
forum: Hardware
---

### Post by Ibrahim mufeed on 2010-07-29
Hi guys,

I have just installed Ubuntu 09.10 on a tablet PC that already have Windows XP. And now I am facing the problem that is the pen moves the pointer but NOT ACCURATE, and it does not click on anything, links, buttons anything.

At the same time, on windows the Tablet PC shows on screen keyboard once you turn the computer on, but on Linux it does not even I checked that the OnBoard software is already installed. 

I need to connect a mouse and a keyboard to access my computer, and I need to use the pen.

Any idea.. I will be thankful.

Regards,

---

### Post by Favux on 2010-07-29
Hi Ibrahim mufeed,

What tablet pc do you have?  It's sounds like the driver isn't grabbing the digitizer.

---

### Post by Ibrahim mufeed on 2010-07-31
HiFavux,

Honestly, this tablet PC is not mine it is for my Dr. in the collage, and it is not a known type, it is made in China and I can not even figure out the name of the brand. It is all written in Chinese language.

---

### Post by Favux on 2010-07-31
Let's see if we can find a name.  In a terminal enter:
```
xinput --list
```
or
```
grep -i name /proc/bus/input/devices
```
or
```
ls -la /dev/tablet-event
```


For the onscreen keyboard you may want CellWriter.

---

### Post by Ibrahim mufeed on 2010-07-31
Ok, here is the output for the first command:

```
salhieh@salhieh-laptop:~$ xinput --list
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
"AT Translated Set 2 keyboard"	id=2	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"HID 04d9:1203"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Aiptek"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 7
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 2499
		Resolution is 10000
	Axis 1 :
		Min_value is 0
		Max_value is 1874
		Resolution is 10000
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 10000
	Axis 3 :
		Min_value is 0
		Max_value is 511
		Resolution is 10000
	Axis 4 :
		Min_value is -128
		Max_value is 127
		Resolution is 10000
	Axis 5 :
		Min_value is -128
		Max_value is 127
		Resolution is 10000
	Axis 6 :
		Min_value is 0
		Max_value is 0
		Resolution is 10000
"Power Button"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=6	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"HID 04d9:1203"	id=7	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"ImPS/2 Generic Wheel Mouse"	id=9	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 7
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
"Macintosh mouse button emulation"	id=10	[XExtensionPointer]
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
"SIGMACH1P U+P Mouse"	id=8	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 7
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

```

And I do not know what to do then :( .

---

### Post by Favux on 2010-07-31
OK, it looks like it may be an Aiptek tablet:
```
"Aiptek"	id=4	[XExtensionKeyboard]

```
In Synaptic Package Manager install the xserver-xorg-input-aiptek package.  Those should be the drivers you need.  I wasn't aware they made a tablet pc.  What is it's name and model number?

---

### Post by Ibrahim mufeed on 2010-08-03
Dear Favux,

Thank you so much for your help.. It was really useful for me.

Regards,

---

