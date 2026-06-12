---
title: "Using synclient- but with 2 touchpads"
date: 2009-02-07
forum: Hardware
---

### Post by FokkerCharlie on 2009-02-07
Hello!

I have a laptop that has a nice touchpad, and also some media 'keys' on the side of the keyboard, which is, in fact a second touchpad.  So, effectively, there's 2 touchpads.

Now, that's fine, and it's all working nicely.  However, I'd like to see if there's a possibility of using multi-touch on my proper touchpad.  Unfortunately, when I run 'synclient -m 10', the utility monitors the media keys- ie the WRONG touchpad!  So how do I get it to look at the right one?

Thanks in advance!
Charlie

---

### Post by FokkerCharlie on 2009-02-07
For info, here's the output from xinput list:

```
$ xinput list
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
"SynPS/2 Synaptics TouchPad"	id=3	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
"SynPS/2 Synaptics TouchPad"	id=4	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
"AT Translated Set 2 keyboard"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
```

---

### Post by FokkerCharlie on 2009-02-09
Bump!

Any ideas?  Go on!  Someone must have some expertise in this area.

Charlie

---

### Post by FokkerCharlie on 2009-02-12
Bump...

one more try.

---

