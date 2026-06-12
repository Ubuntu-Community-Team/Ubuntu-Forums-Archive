---
title: "disable tap"
date: 2004-11-06
forum: Hardware &amp; Laptops
---

### Post by haynest on 2004-11-06
Greetings...

I have a Dell Latitude 505. I would like to disable tap on the touchpad. The mouse jumps around as I type, and it drives me nuts. There may be some easy way to do this, and I am just not seeing it.

Regards...   Tom

---

### Post by knappen on 2004-11-06
Under input device, try to add 

	Option		"TapButton1"		"0"

in the etc/X11/XF86Config-4 file.

My section looks like this

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
	Option		"TapButton1"		"0"
EndSection

Hope it helps.

---

### Post by haynest on 2004-11-06
I added the line, restarted X and it does not seen to have made any difference.

I have two mice defined. Do you think that might be the problem?

I tried commenting out the other, but then X couldn't find a screen...

---

