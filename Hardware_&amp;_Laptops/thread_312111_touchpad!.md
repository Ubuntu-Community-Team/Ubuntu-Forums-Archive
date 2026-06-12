---
title: "touchpad!"
date: 2006-12-03
forum: Hardware &amp; Laptops
---

### Post by Mazen on 2006-12-03
hi all, 
can someone tell me why my touchpad sometimes works and sometimes not!? it works like once a month or something for no particular reason.
i have a toshiba laptop and in my xorg.conf it says it's a Synaptics touchpad..
this is the section of the xorg:

```
Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
	Option	    "SHMConfig" "1"
EndSection
```

---

### Post by ciscosurfer on 2006-12-03
I'm not totally sure of an answer for you, but you may find this helpful: gsynaptics ([http://www.getdeb.net/category.php?id=37](http://www.getdeb.net/category.php?id=37))

---

### Post by spx3 on 2006-12-03
hey mazen,i had your problem,similar one
but with the usb mouse not with the touchpad
i also have a toshiba laptop
here is [http://ubuntuforums.org/showthread.php?t=311462](http://ubuntuforums.org/showthread.php?t=311462)
at the end of the thread you will find my xorg.conf
you can take the section for "Synaptics Touchpad" from
there and see if it works
but be carefull!!! make a backup of your xorg.conf first!

---

