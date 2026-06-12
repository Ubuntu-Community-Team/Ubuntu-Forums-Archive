---
title: "[ibex] lost control of touchpad in Compaq Evo N610c"
date: 2008-11-28
forum: Hardware
---

### Post by ZooLA_IL on 2008-11-28
Hi all,
after updating Intrepid Ibex (cannot remember what package I was downloading) my touchpad stopped working.

Ubuntu doesn't recongnize it. The output of "xinput -list":
```
~$ xinput list
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
"AT Translated Set 2 keyboard"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255

```

also:
```
~$ xinput list-props "SynPS/2 Synaptics TouchPad"
unable to find device SynPS/2 Synaptics TouchPad
```

Investigating the problem I found out that "Synaptic Touchpad" Device is no longer controlled by Xorg.conf. I followed the following instructions:
[HTML]https://help.ubuntu.com/community/SynapticsTouchpad[/HTML]
trying to configure it by HAL fdi file with no success.

I was also trying to enable SHMConfig but since Ubuntu won't recognize the touchpad, it cannot set it on.

I'm asking you're advise! Does anyone have the same problem and manage to solve it?

Thanks.

---

