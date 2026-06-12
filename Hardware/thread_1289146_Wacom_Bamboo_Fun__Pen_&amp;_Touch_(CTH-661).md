---
title: "Wacom Bamboo Fun : Pen &amp; Touch (CTH-661)"
date: 2009-10-12
forum: Hardware
---

### Post by snk00sj on 2009-10-12
I just bought a new wacom tablet. I figured that if other bamboo's are auto recognised in jaunty i wouldn't have a problem getting this to work.

That's not the case.

After trying various tutorials (wiki/forums) i am running out of options here. I don't know where the problem is, but i think it starts with ubuntu not recognising the device as a "wacom" board.


```

dpkg -l | grep wacom
ii  wacom-tools                                1:0.8.4.1-0ubuntu3                               utilities for Wacom tablet devices
ii  xserver-xorg-input-wacom                   1:0.8.4.1-0ubuntu3                               X.Org X server -- Wacom input driver

```

dmesg (when plugging in)
```

[ 1390.108015] usb 6-2: new full speed USB device using uhci_hcd and address 2
[ 1390.276658] usb 6-2: configuration #1 chosen from 1 choice

```

lsusb
```

lsusb
Bus 006 Device 002: ID 056a:00d3 Wacom Co., Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 008: ID 0424:223a Standard Microsystems Corp. 8-in-1 Card Reader
Bus 003 Device 007: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 003 Device 006: ID 0424:2502 Standard Microsystems Corp. 
Bus 003 Device 005: ID 1532:0001 Razer USA, Ltd RZ01-020300 Optical Mouse [Diamondback]
Bus 003 Device 004: ID 046d:c50c Logitech, Inc. Cordless Desktop S510
Bus 003 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

xinput list
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
"Logitech USB Receiver"	id=2	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 16
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
"Power Button"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Logitech USB Receiver"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
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
"Razer Razer 1600dpi Mouse"	id=7	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 15
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

Anyone have an idea what to try, howto get this running ?

---

### Post by Favux on 2009-10-12
Hi snk00sj,

I gather you have the new tablet that supports touch combined with a Bamboo.  Right now the multi-touch isn't supported.  The linuxwacom in Jaunty, 0.8.2-2, is too old to recognize your tablet.  For example the wcmUSB.c has a table of Vendor and Product ID's which I'm sure your tablet isn't in.  I don't know if the latest 0.8.4-3 has it in but I know Ping at the LWP said he'd be adding it.  So if it isn't in there it should be shortly.

Some others have posted about your tablet at LWP's forums general discussion and development traffic linked here:  [http://linuxwacom.sourceforge.net/index.php/main](http://linuxwacom.sourceforge.net/index.php/main)

---

### Post by Nausser on 2009-10-24
It will be a couple releases before we see anything move forward with touch support. Likely nothing until version 0.8.6 That's the word for now anyways.

---

### Post by Favux on 2009-10-24
Hi snk00sj and Nausser,

Just to update you we nearly have the CTH-661 working on this thread:  [http://ubuntuforums.org/showthread.php?t=1290251](http://ubuntuforums.org/showthread.php?t=1290251)

Since the latest Xorg includes MPX I think multi-touch is possible for Lynx.

---

