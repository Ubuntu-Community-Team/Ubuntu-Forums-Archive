---
title: "Wacom Graphire 4, pad button and scroll wheel"
date: 2009-07-06
forum: Hardware
---

### Post by AvixK7 on 2009-07-06
Hi all,

I have a wacom graphire 4 that's working pretty well on Jaunty. the pen and pressure sensitivity is working fine without any config. However, the pad buttons, eraser and scroll wheel are not working.

I've read that this is supposedly because of the switch to HAL, and no longer using X.org?

Any way to get the button and scroll wheel working? It would make things easier on some projects I'm working on :)

thanks.

---

### Post by Favux on 2009-07-06
Hi AvixK7,

I don't know quite where you are in terms of setting up.  Have you been able to use wacomcpl?  And have you tried setting up through the .xinitrc it generates?

If wacomcpl isn't working for you, you're encountering the problem with the default Jaunty 10-wacom.fdi.  It's not parsing the HAL names into linuxwacom names.  To see this in a terminal type:
```
xsetwacom list
```
That should return wacom names like stylus, eraser, cursor, and pad.  If it's blank, to see the names it is returning enter:
```
xinput --list
```
You could rename everything in .xinitrc or you could substitute a wacom.fdi that does parse the names correctly.  Assuming the Graphire4 is a usb table, which I believe it is.

For the new .fdi see post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

Then to set up wacomcpl see Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

Then to set up your pad see shatterblast's examples for a Bamboo on post #188 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=19](http://ubuntuforums.org/showthread.php?t=967147&page=19)  You'll probably have to adapt them some for the Graphire4.

And if you want the page before the .fdi post shows you how to put the settings in .fdi syntax.

Good luck!

---

### Post by AvixK7 on 2009-07-07
thanks for the suggestions. I'm at work at the moment, but I'll let you know if it helps soon enough :)

---

### Post by AvixK7 on 2009-07-07
I followed your first two terminal commands and got this input:

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
"Wacom Graphire4 6x8"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 16704
		Resolution is 2032
	Axis 1 :
		Min_value is 0
		Max_value is 12064
		Resolution is 2032
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
"Wacom Graphire4 6x8 pad"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 2
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 16704
		Resolution is 2032
	Axis 1 :
		Min_value is 0
		Max_value is 12064
		Resolution is 2032
	Axis 2 :
		Min_value is 0
		Max_value is 511
		Resolution is 1
	Axis 3 :
		Min_value is 0
		Max_value is 0
		Resolution is 1
	Axis 4 :
		Min_value is 0
		Max_value is 0
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Wacom Graphire4 6x8 cursor"	id=6	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 16704
		Resolution is 2032
	Axis 1 :
		Min_value is 0
		Max_value is 12064
		Resolution is 2032
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
"Wacom Graphire4 6x8 eraser"	id=7	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 16704
		Resolution is 2032
	Axis 1 :
		Min_value is 0
		Max_value is 12064
		Resolution is 2032
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
"Logitech USB-PS/2 Optical Mouse"	id=8	[XExtensionPointer]
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

```

I did a fresh install of Jaunty after sticking with hardy and skipping Intrepid so I may have missed some changes as to how things are configured. 

I initially assumed I would need to simply change the x.org config file. 

could you explain what the ".fdi" is, and what is .xinitrc 

thank you kindly :)

---

### Post by Favux on 2009-07-07
Hi AvixK7,

HAL is naming:

stylus = "Wacom Graphire4 6x8"
eraser = "Wacom Graphire4 6x8 eraser"
etc.

Since those aren't linuxwacom names like stylus, eraser, cursor, and pad, that's why xsetwacom commands and wacomcpl won't work.

HAL is hardware abstraction layer and .fdi is file device information.  The idea is to allow usb hotplugging.  They started the transition in Intrepid.  If you use xorg.conf you lose hotplugging, plus they are deprecating it.

The .xinitrc is the hidden file wacomcpl generates in your "/home/username/" directory with all of the xsetwacom commands necessary to configure your tablet.

---

