---
title: "jaunty : gateway c120x, no wacom, tried instructions"
date: 2009-08-05
forum: Hardware
---

### Post by piusvelte on 2009-08-05
I have a gateway c120x, which has a touchscreen. I'm starting from a clean install of jaunty, with updates installed. It appears that this model is supported in ubuntu, and I've reviewed [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom), which states that wacom is supported out of the box. The wacom device is listed when I run lsusb. I installed xserver-xorg-input-wacom and wacom-tools and rebooted, but the touchscreen still doesn't work. wacomcpl doesn't list any devices, though it appears from various posts that it probably wouldn't. I checked xorg.conf, which doesn't include any lines for wacom, but the help page above says that wacom is not configured by x11 in jaunty. This is a fresh new install, so I can try reinstalling again if necessary. What am I missing to get this working? Thank you!

---

### Post by Favux on 2009-08-05
Hi piusvelte,

The c120x has a Wacom digitizer with a touch screen correct?  What we need to know is if the internal connection from the digitizer is usb or serial.  Do you know?  If not try in a terminal:
```
dmesg | grep [Ww]acom
```
Can you show me the Wacom section of lsusb?  And it's a new fresh install of Jaunty, correct?

---

### Post by piusvelte on 2009-08-05
Favux, thank you for your reply. I thought that it was usb, but I'll check when I get home in 2hrs. Thanks again!

EDIT: Yes, a new install. I install from CD last night, and installed all updates.

---

### Post by Favux on 2009-08-05
Hi piusvelte,

OK, from what you're saying:
```
xsetwacom list
```
should be blank.  But:
```
xinput --list
```
might be useful.

---

### Post by piusvelte on 2009-08-05
Here's the output:

```

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 056a:0093 Wacom Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$ dmesg |grep [Ww]acom
[   12.380505] wacom: probe of 2-2:1.0 failed with error -113
[   12.382880] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/input/input7
[   12.384175] usbcore: registered new interface driver wacom
[   12.384218] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver

$ xsetwacom list

$ xinput --list
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
"Wacom ISDv4 93"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 26212
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 16420
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 255
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
"Video Bus"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Wacom ISDv4 93 pad"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 1
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 26212
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 16420
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
	Axis 3 :
		Min_value is 0
		Max_value is 4095
		Resolution is 1
	Axis 4 :
		Min_value is 0
		Max_value is 4095
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"AT Translated Set 2 keyboard"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Wacom ISDv4 93 cursor"	id=6	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 26212
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 16420
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 255
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
"Wacom ISDv4 93 eraser"	id=7	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 26212
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 16420
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 255
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
"Macintosh mouse button emulation"	id=8	[XExtensionPointer]
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
"SynPS/2 Synaptics TouchPad"	id=9	[XExtensionPointer]
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

---

### Post by Favux on 2009-08-05
Hi piusvelte,

OK, from what I see I'm pretty sure it's usb.  We could mess around a bit more with "lshal" generating a text file "lshal>lshal.txt".  Which you could open with gedit and search "Wacom", etc. with Find.

Given it's usb you want to follow gali98's tutorial on post #104 on this thread:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  Read Jaunty Users near the top and follow the link in 1) to gali98's Jaunty HOW TO.  When you've finished you can complete setting up wacomcpl by following Section 3 on the first HOW TO.

Good luck!

---

### Post by piusvelte on 2009-08-05
Thank you very much Favux, I'm off to try out the tutorial.

UPDATE: Everything is working fine now, thank you! I compiled the module, copied it, created the fdi file, using the posted starting point and rebooted.

---

### Post by Favux on 2009-08-05
Hi piusvelte,

Outstanding!  Good job.  I agree, you want the basic .fdi, because your calibrations are probably different and you can configure through wacomcpl.  You're welcome.

---

