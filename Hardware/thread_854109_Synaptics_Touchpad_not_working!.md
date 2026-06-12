---
title: "Synaptics Touchpad not working!"
date: 2008-07-09
forum: Hardware
---

### Post by sillybilly913 on 2008-07-09
I installed Ubuntu Hardy Heron on my XPS M1530 with Wubi and the install went great, everything seemed to be working beautifully BUT...

then I realized I had no mouse. Agh! I know that I have a Synaptics Touchpad because that's what it shows up as in Windows. I used the following community article...

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) 

...to try and edit my "/etc/x11/xorg.conf" file, but for some reason when I tried to save my xorg.conf changes, it told me: 

"Could not save the file /etc/x11/xorg.conf. You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

I even looked at and re-opened the file in the GNOME browser. I have no idea why I wouldn't have permission to edit, as I'm the only user account that exists. I also need to enable SHMConfig with this file, but the point is I want my touchpad and so far I have zilch.

---

### Post by sillybilly913 on 2008-07-09
Oops... almost forgot, here's a copy of what my xorg.conf file looks like...

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by RichardG891 on 2008-07-09
You need to access the file as root. From the command line:

[COLOR="YellowGreen"]username@location:~$[/COLOR] sudo gedit /etc/x11/xorg.conf

or, if you prefer, navigate and select the file with the file browser launched as root:

[COLOR="YellowGreen"]username@location:~$[/COLOR] sudo nautilus

---

### Post by RichardG891 on 2008-07-09
Sorry - the first target should be "/etc/[COLOR="Blue"]X11[/COLOR]/xorg.conf" not /etc/[COLOR="Blue"]x11[/COLOR]/xorg.conf.

---

