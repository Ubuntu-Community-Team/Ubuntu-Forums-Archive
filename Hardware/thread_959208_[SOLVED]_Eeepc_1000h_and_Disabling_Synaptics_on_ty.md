---
title: "[SOLVED] Eeepc 1000h and Disabling Synaptics on typing"
date: 2008-10-26
forum: Hardware
---

### Post by Triggerhapp on 2008-10-26
Before we start, I will state that I know "A thing or two" About how to do this on your average laptop.

First step is adding Option "SHMConfig" "True" (or "on", depending on your source) to the Synaptic section of your xorg.conf and then restarting X.

Then you can run syndaemon or g/q/k synaptics.

Sounds simple doesn't it?

One my Eeepc this seems to get me no-where.

syndaemon and gsynaptics both mutter about SHMConfig not bieng set. Also on futher note xinput has lead me to believe (although im no pro!) that my synaptic touchpad is bieng read as a standard mouse (which doesn't explain why I can still scroll with it)

Here some of the usual suspects, Let me know if more info is needed :

/etc/X11/xorg.conf
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
        Option          "SHMConfig" "True"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
        Option		"SHMConfig"		"True"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
        Option "AccelMethod" "exa"
        Option "MigrationHeuristic" "greedy"
        Option "ExaNoComposite" "false"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad" 
EndSection

```

the begining of .xsession-errors (Truncated to skip the pointless errors im causing ;) )
```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/startxfce4: X server already running on display :0
xrdb:  "Xft.hinting" on line 9 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 10 overrides entry on line 7
** Message: Querying XF86Misc extension
** Message: XF86Misc extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: Querying XINPUT extension
** Message: XINPUT extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27ae (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x600) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Can't access shared memory area. SHMConfig disabled?
Conky: desktop window (57) is root window
Conky: window type - normal
Conky: drawing to created window (1a00002)
Conky: drawing to double buffer

```

$ xinput list
```

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
"Generic Keyboard"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Configured Mouse"	id=3	[XExtensionPointer]
	Num_buttons is 9
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

Any help is Greatly appreaciated.
~Trigg

---

### Post by Triggerhapp on 2008-10-26
Found the help on IRC!

For those of you who do not know how to fix this its here:

edit the file /etc/modprobe.d/psmouse (will need sudo)
```

options psmouse elantech=1

```

Create the empty file and add this line.
Reboot and continue with any other guide about how to configure your synaptic touchpad.

Thanks to LjL for the answer

---

