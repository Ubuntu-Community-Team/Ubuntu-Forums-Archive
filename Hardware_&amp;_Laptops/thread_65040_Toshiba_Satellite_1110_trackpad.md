---
title: "Toshiba Satellite 1110 trackpad"
date: 2005-09-12
forum: Hardware &amp; Laptops
---

### Post by Steve Smith on 2005-09-12
The trackpad on my Toshiba Satellite 1110 works, but the vertical scroll doesn't.  I've added the vertscrolldelta line to xorg.conf, but it didn't work:

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
	Option		"VertScrollDelta"	"100"
EndSection

```

Does anyone know if Toshiba trackpads are Synaptics compatible?

---

### Post by Steve Smith on 2005-09-15
I'm bumping this up after 3 days, anyone have any ideas?!

**Edit:**
I've installed tpconfig.  When I run tpconfig -i it returns:
fatal: Could not open PS/2 Port [/dev/psaux]

Is the touchpad using ps/2?!

---

### Post by jeegiz on 2005-09-16
I guess you actually have alps touchpad, which is compatible with synaptics, but vertical scroll does not work. If you have kernel < 2.6.11 you have to patch synaptics driver code (see /usr/share/doc/xorg-driver-synaptics directory).  I think from the 2.6.11 it is already included in kernel. 

Personally me (also with toshiba alps touchpad) is waiting for the breezy, where vertical scroll should work out of the box.

---

### Post by Steve Smith on 2005-09-16
[QUOTE=jeegiz]Personally me (also with toshiba alps touchpad) is waiting for the breezy, where vertical scroll should work out of the box.[/QUOTE]
Now that sounds like a plan, thanks!

---

