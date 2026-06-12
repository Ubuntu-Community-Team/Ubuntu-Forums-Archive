---
title: "microsoft xbox controller acting as mouse"
date: 2008-11-13
forum: General Help
---

### Post by desolatordan on 2008-11-13
Upgraded to 8.10, and am having problems with xbox controllers. I only use my linux box for game console emulation, with xbox controllers, so it's quite important that they work. They don't register any input in SDL or jscalibrator. But the analog stick moves the mouse around the screen. Other logitech controllers work fine, but xbox controllers cannot be used.

Is there a temporary workaround for this bug? I search for a way to downgrade to 8.04 and saw none. I had to compile a few programs rather than using a package, if I save those somehow and do a reinstall of 8.04, will they still work?

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/277915](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/277915)

---

### Post by eleniontolto on 2008-11-14
I also am having this problem :(

---

### Post by desolatordan on 2008-11-17
Does anyone have a functional xbox controller in 8.10?

---

### Post by desolatordan on 2008-11-22
Bump.

---

### Post by illissius on 2008-11-28
How to make it work:

$ xinput list
See which device number the Xbox controller has
$ xinput set-int-prop THATDEVICENUMBER 'Device Enabled' 32 0

Could someone with a launchpad account also post it to the bug? Don't feel like making one. Thanks.

---

### Post by desolatordan on 2008-11-30
> $ xinput list
See which device number the Xbox controller has
$ xinput set-int-prop THATDEVICENUMBER 'Device Enabled' 32 0


Works great! Thanks. I posted your workaround to the LaunchPad report.

---

### Post by Asday on 2009-01-05
> **illissius said:**
> How to make it work:

$ xinput list
See which device number the Xbox controller has
$ xinput set-int-prop THATDEVICENUMBER 'Device Enabled' 32 0

Could someone with a launchpad account also post it to the bug? Don't feel like making one. Thanks.

With the second command, I get this output:

```
usage :
	xinput get-feedbacks <device name>
	xinput set-ptr-feedback <device name> <threshold> <num> <denom>
	xinput set-integer-feedback <device name> <feedback id> <value>
	xinput set-button-map <device name> <map button 1> [<map button 2> [...]]
	xinput set-pointer <device name> [<x index> <y index>]
	xinput set-mode <device name> ABSOLUTE|RELATIVE
	xinput list [--short || <device name>...]
	xinput query-state <device name>
	xinput test [-proximity] <device name>
	xinput version 
	xinput list-props <device> [<device> ...]
	xinput set-int-prop <device> <property> <format (8, 16, 32)> <val> [<val> ...]
	xinput watch-props <device>
	xinput delete-prop <device> <property>

```

What's going on?

---

### Post by clintonthegeek on 2009-01-07
You just typed it in wrong. Make sure you're using the id=x part of the first list to get the right device number. Also remember the quotes, and spaces around the last two numbers. :)

---

### Post by Asday on 2009-01-07
The only thing that could possibly be that is if I'm meant to type "id=6" as opposed to "6" for "THATDEVICENUMBER".

---

### Post by razar45 on 2009-01-07
omg it worked! awesome

---

### Post by k69 on 2009-02-21
Is this for wired or wireless controllers  because I'm just getting unable to find device

thanks for any help in advance

---

### Post by Asday on 2009-02-21
For me it was wired.  Just plugged the bugger into USB.

---

### Post by k69 on 2009-02-21
I'm useing wireless, guess that would be a handy bit of info lol

---

### Post by Asday on 2009-02-22
Well in that case I'm lost.  Does it recognise the wireless adapter (for the controller) when you plug it in?

---

### Post by k69 on 2009-02-24
Pretty sure it doesn't recognise that a new device is attatched because I cant find the reciver anywhere, but, i can move the mouse cursor with the controller just no button support at all and the cursor always returns to center. this is what i get no mater what id number i give it.

k69@NERV:~$ xinput list
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
"PS/2 Logitech TrackMan"	id=3	[XExtensionPointer]
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
"AT Translated Set 2 keyboard"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Xbox 360 Wireless Receiver"	id=5	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is -32768
		Max_value is 32767
		Resolution is 10000
	Axis 1 :
		Min_value is -32768
		Max_value is 32767
		Resolution is 10000
"Xbox 360 Wireless Receiver"	id=6	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is -32768
		Max_value is 32767
		Resolution is 10000
	Axis 1 :
		Min_value is -32768
		Max_value is 32767
		Resolution is 10000
"Xbox 360 Wireless Receiver"	id=7	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is -32768
		Max_value is 32767
		Resolution is 10000
	Axis 1 :
		Min_value is -32768
		Max_value is 32767
		Resolution is 10000
"Xbox 360 Wireless Receiver"	id=8	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is -32768
		Max_value is 32767
		Resolution is 10000
	Axis 1 :
		Min_value is -32768
		Max_value is 32767
		Resolution is 10000
k69@NERV:~$ xinput set-int-prop id=5 'Device Enabled' 32 0 
unable to find device id=5
k69@NERV:~$

---

### Post by TheIdiotThatIsMe on 2009-04-12
Worked like a charm. Thanks a bunch :-)

---

### Post by prahs rozar on 2009-04-13
k69:
Just put in the number, e.g. x not id=x. Then it should work.

---

### Post by MNubbe on 2009-08-23
Wow, this worked. Thanks!

---

