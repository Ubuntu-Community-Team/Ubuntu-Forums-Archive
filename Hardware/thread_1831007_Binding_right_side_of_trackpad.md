---
title: "Binding right side of trackpad"
date: 2011-08-22
forum: Hardware
---

### Post by Ambivalent_Echo on 2011-08-22
Hello everyone, I was wondering if anyone could help me with binding the right side of my trackpad. I currently have this for the 50-synaptics.conf file
```

Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
	Option		"Butons"		"11"
	Option 		"LTCornerButton" 	"2"
	Option 		"LBCornerButton" 	"8"
	Option 		"RBCornerButton" 	"10"
	Option 		"RTCornerButton" 	"11"
EndSection
```I don't know if you can just put it to button 10/11 like that but I've tried binding them to 2/3 but for some reason only the right side will not work. The left side seems to be working fine though. I imagine that it has something to do with the edge scroll, but even when disabling edge scroll through the ubuntu system settings program it still will not work.

Ultimately I want to bind those two buttons to the expose and spread views in ubuntu, so if anyone even knows another way to do that this issue would be moot. I'm a relative newbie to linux but I can get my hands dirty in some config files.

Thanks for any help everyone.

---

