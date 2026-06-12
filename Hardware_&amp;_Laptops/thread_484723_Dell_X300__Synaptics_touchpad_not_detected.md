---
title: "Dell X300 : Synaptics touchpad not detected"
date: 2007-06-26
forum: Hardware &amp; Laptops
---

### Post by EnderEOC on 2007-06-26
Hello.
I'm new to linux and Ubuntu.
So far i'm really happy BUT one issue...
I have a Dell X300 which use a Synaptics touchpad (I use the synaptics drivers and soft under windows xp without any issues).
But somehow, it isn't detected under Ubuntu.
In the xorg.conf, i had only this at first (about mouse) :

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

So i added :

Section "InputDevice"
	Identifier "Synaptics Touchpad"
	Driver "synaptics"
	Option "Device" "/dev/psaux"
	Option "Protocol" "auto-dev"
	Option "SHMConfig" "true"
	Option "SendCoreEvents" "true"
EndSection

Unfortunatly, it is not enough to make gsynaptics soft works.
It keeps saying i need to add the "SHMConfig" "true" line.
It also does it for a friend who has a Dell D600, but his touchpad was entered correctly in xorg.conf.
If anyone has any idea, please help.

---

### Post by PaulFr on 2007-06-26
While I have no experience with the touchpad, the link I checked said **> Option "SHMConfig" "on"** not **> Option "SHMConfig" "true"**

See **[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)**. Hope this helps.

---

### Post by EnderEOC on 2007-06-26
Thx a lot it worked :)
The thing that was missing is the line ' InputDevice	"Synaptics Touchpad" ' in the server layout section.
Thx again i can finaly disable the click by the touchpad :D

---

