---
title: "Netbook Touchpad not Responding"
date: 2009-10-30
forum: Hardware
---

### Post by 5BallJuggler on 2009-10-30
Hi All,

I cant get the touchpad to work on the wife's Acer Aspire One, I have the same type of netbook, and it works fine

I upgraded to a beta version of 9.10 on my netbook about a week ago and had no issues with the touchpad at all, but when I installed the official release on to the wife's it caused the touchpad to stop working,
tried the usual Fn+F7, to no avail. 

I made a startup USB of 9.10 and tried that and it was all OK, 
it is also OK using a bluetooth mouse.

This is my "xinput list" output
```
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
"USB 2.0 Camera"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Sleep Button"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=6	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=7	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=8	[XExtensionPointer]
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
"SynPS/2 Synaptics TouchPad"	id=9	[XExtensionPointer]
	Type is TOUCHPAD
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

```

This is my wife's
```
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
"MLK Keyboard Mouse Set"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
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
"MLK Keyboard Mouse Set"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Sleep Button (CM)"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button (CM)"	id=6	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=7	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button (FF)"	id=8	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=9	[XExtensionPointer]
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

```

I think it's missing this, but I don't know how to fix
```
"SynPS/2 Synaptics TouchPad"	id=9	[XExtensionPointer]
	Type is TOUCHPAD
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
```

I really hope someone can help me, she may just kill me when she finds out

Thanks 
Phil

---

### Post by 5BallJuggler on 2009-10-30
bump

---

### Post by 5BallJuggler on 2009-10-30
Fixed by calling a previous linux kernel in menu.lst

change default call from 2 to 0

was calling this
Ubuntu 9.10, kernel 2.6.28-15-generic

now calling this
Ubuntu 9.10, kernel 2.6.31-14-generic
 

Hope this helps someone else.
:D

---

### Post by MiloszK on 2009-11-01
That's a cool trick with the xinput list. I found that I'm missing a touchpad entry in mine as well. The folks in _[this thread]("http://ubuntuforums.org/showthread.php?p=8216841#post8216841")_ are discussing the same problem, with different solutions, but none work for me. Did you stick with your solution of reverting to the previous kernel, or have you found a more specific solution since?

---

### Post by 5BallJuggler on 2009-11-01
> **MiloszK said:**
> That's a cool trick with the xinput list. I found that I'm missing a touchpad entry in mine as well. The folks in _[this thread]("http://ubuntuforums.org/showthread.php?p=8216841#post8216841")_ are discussing the same problem, with different solutions, but none work for me. Did you stick with your solution of reverting to the previous kernel, or have you found a more specific solution since?

still using the specified kernel, it is actually the letest one, i don't know why it wasn't automatically set-up.

---

### Post by MiloszK on 2009-11-01
OH good call. You wrote:

2.6.28-15-generic
2.6.31-14-generic

I read:

bunchofnumbers-15-sometext
bunchofnumbers-14-sometext

I gotta read more carefully! :D

Thank you very much!

---

### Post by Rudy246 on 2009-11-05
Hm, I tried editing my menu.lst in /boot/grub, and changed the kernel numbers from

2.6.28.15-generic
to
2.6.31.14-generic

But forgot to change the 9.04's to 9.10's, and then rebooted. My Ubuntu now only boots as a terminal with no GUI. I used PICO to edit the menu.lst file to make the 9.04's into 9.10's, but it still only boots to a command line interface when I boot into Ubuntu.

When I try to shut down in the CLI, it gives me some form of recoveery window, asking if I want to update grub boot loader, repair damaged files, etc. I tried updating the grub boot loader, but that didn't fix anything.

I also tried changing the  menu.lst back to the way it was before I even touched it, but it still will now only boot into a CLI.

Any ideas?

---

