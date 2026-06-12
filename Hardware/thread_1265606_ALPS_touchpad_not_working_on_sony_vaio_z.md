---
title: "ALPS touchpad not working on sony vaio z"
date: 2009-09-13
forum: Hardware
---

### Post by RavensKrag on 2009-09-13
So my touchpad just suddenly stopped working one day for no apparent reason.  I had my mouse and touchpad configured through xorg.conf, and I suppose it just decided to stop working.  I first tried using HAL fdi files to configure the touchpad, but that didn't work, other than to allow me to set the shmconfig to "true" and use the gsynaptics utility.  However, that did not activate my touchpad, even with the enable touchpad option on.  I also made sure the option was on under mouse settings.  So I uninstalled the gsynaptics thing because it was not doing anything.  

My mouse is a logitech vx nano, which only has access to 5 buttons when it should have 9.  I can not use the horizontal scroll or the two thumb buttons.  The buttons do not even seem to be registering in xev.  I tried configuring that through a fdi file as well, but it doesn't seem to give my any more buttons.

I suspect that HAL might not be reading my configuration files for some reason.  Though that may not be the case... I'm really just confused because it was working perfectly fine about a week or so ago... Can someone help me please? I'm not extremely skilled with Linux, so step-by-step instructions would be greatly appreciated if at all possible.  Also, let me know if there's more information that I should post.

---

### Post by RavensKrag on 2009-09-17
bump

also, should I be using HAL at all? or should I just go back to modifying xorg.conf?

---

### Post by yotam on 2009-10-17
You may consider trying my Alps driver in
   [http://www.medini.org/software/alps/alps.html]("www.medini.org/software/alps/alps.html")
-- yotam

---

### Post by turtles on 2010-01-06
Same problem here.
Touch pad can be seen if I ```
cat /dev/psaux
```
if I lshal | grep 'touch' 
I get:
```
 info.capabilities = {'input', 'input.mouse', 'input.touchpad'} (string list)

```

xinput list :
```

xinput list
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
"Sleep Button (CM)"	id=2	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button (FF)"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"PS/2 Mouse"	id=5	[XExtensionPointer]
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
"Macintosh mouse button emulation"	id=6	[XExtensionPointer]
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
"Logitech N48"	id=7	[XExtensionPointer]
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

IF I ```
grep 'EE' /var/log/Xorg.0.log
```
I get:
(EE) AlpsPS/2 ALPS GlidePoint Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "AlpsPS/2 ALPS GlidePoint"
(EE) config/hal: NewInputDeviceRequest failed (8)


EDIT:
I just noticed I booted the wrong kernel after upgrade.
If you have a similar problem run [code]uname -a[code]
and check your kernel.
Editing /boot/grub/menu.lst to boot the latest kenrl in /boot/ 
solved this.
Thanks

---

