---
title: "Please help with an interesting little problem"
date: 2009-04-26
forum: Hardware
---

### Post by FokkerCharlie on 2009-04-26
Hello!

I have an Acer Aspire 5920G laptop that works well with Ubuntu.  There's one feature, however, that is causing a bit of a headache.

On the right-hand side of the keyboard, there are 4 touch-sensitive keys for controlling media- Play/Pause, Stop, Rwd, Fwd.  This device is detected by Ubuntu as an extra touchpad.  So, it works out of the box, but the keys are mapped as 4,5,6,7 which is the snag.  Pressing them causes scrolling to happen, as if I were using the main touchpad.

We have been getting around this in Intrepid using this line in 'Sessions':

```
xinput set-button-map "4" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16
```

Which worked fine (see this thread: [http://ubuntuforums.org/showthread.php?t=997860]("http://ubuntuforums.org/showthread.php?t=997860")) .  Unfortunately, since the upgrade to Jaunty, the device number (previously 4 as above) has been variable, depending on other devices.  For instance, I usually use a Logitech trackball, so here's the output from xinput list with my normal setup:

```
~$ xinput list
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
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=3	[XExtensionPointer]
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
"Logitech USB Receiver"	id=4	[XExtensionPointer]
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
"SynPS/2 Synaptics TouchPad"	id=5	[XExtensionPointer]
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
"SynPS/2 Synaptics TouchPad"	id=6	[XExtensionPointer]
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

So in this case 

```
xinput set-button-map "5" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16
```

Would work.  However, here's the output when the trackball is removed:

```
~$ xinput list
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
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=3	[XExtensionPointer]
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
"SynPS/2 Synaptics TouchPad"	id=4	[XExtensionPointer]
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
"SynPS/2 Synaptics TouchPad"	id=5	[XExtensionPointer]
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

So "4" would be the correct device to target.  This all means that it's not possible to cover all the bases with the one-liner in 'Startup Apps' any more.  So, here's how I see a potential solution:

1) Somehow change the name of the media keys device from "SynPS/2 Synaptics TouchPad" to something else, like "Media Keys".  Any idea how to do that, bearing mind that there's two of them?!

2) A script to exmamine the output from xinput list, find the first touchpad in the list, and apply the button re-map to the correct identifier.  I think this would be possible, but I am well short of the scripting prowess that would be required here!

3) Something else!  Any ideas?

Your input is appreciated, I know that this is a glitch that affects a lot of people, we'd all love to get it cracked!

Cheers
Charlie

EDIT- it looks even more problematic than first thought.  It seems that the media keys device isn't always the first one listed by xinput.  Aaaaargh!  Heeeeeellllpppp!

---

### Post by StuartN on 2009-04-26
> **FokkerCharlie said:**
> ```
xinput set-button-map "4" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16
```

Can you not use the name, e.g. xinput set-button-map "SynPS/2 Synaptics TouchPad" instead of the ID?

---

### Post by FokkerCharlie on 2009-04-26
Ah-ha!

Here is the problem- there are two touchpads, both with the same name, so trying that returns a message asking me to use the device ID instead!

Boo!

Charlie

---

### Post by StuartN on 2009-04-26
> **FokkerCharlie said:**
> Here is the problem- there are two touchpads, both with the same name, so trying that returns a message asking me to use the device ID instead!

There is probably some clever way to grep the output for the name and list the first (or second) ID number, but I'm not into tricky scripting - I could get as far as:
```
xinput list | grep Synaptics | head -1 | grep -o id=.| tr -d id=
```
which would give the output "4" (if that is the first Synaptics device). Substituting tail -1 would give the id of the last. So I guess you could try:
```
xinput set-button-map "`xinput list | grep Synaptics | head -1 | grep -o id=. | tr -d id=`" 4 ....
```
Try the first command step by step, when you get the right ID number out of it then insert it into the second command, enclose in backward single quotes ` (and the double quotes for the xinput set-button-map command).
Sorry it isn't very elegant, but it should work.

---

### Post by FokkerCharlie on 2009-04-26
StuartN

You might just be the man.  This is what is working at the moment:

```
xinput set-button-map "`xinput list | grep Synaptics | tail -1 | grep -o id=. | tr -d id=`" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16
```

As it seems that the second listed touchpad is the one that needs to be tweaked.  I'll have a test now with re-booting without my trackball, but in the meantime- very many thanks indeed!

Charlie

EDIT:  Yes, it worked on re-start, but I had to pop the line in a script, rather than just sticking it in Startup Apps.  Don't know why, but it's no problem.

Cheerio!
Charlie

---

