---
title: "turning off clicks in the corners of my touchpad"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by racyrefinedraj on 2007-06-14
I've got a toshiba M35x equipped with a synaptics touchpad, and I'm currently running Dapper.  I love the vertical scroll along the righthand edge (forgot if that came default or if I had to do something to enable it), but I am infuriated by the fact that touching the upper-right corner causes a middle click and touching the lower-right corner causes a right click. I'd like to turn the "clicks in the corners" off, but keep the "scroll on the side."

I tried opening up /etc/X11/xorg.conf, but there's no obvious option to diable

here's the relevant part of my xorg.conf file:

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

```

Thanks so much.

---

### Post by brettr on 2007-06-14
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SingleTapTimeout"      "0"
        Option          "ClickTime"             "0"
        Option          "SHMConfig"
        Option          "LockedDrags"           "1"
EndSection

```

So what you probably want to do is have the SHMConfig option set. Then you can go onto a terminal and do ```
synclient -l
``` and it will show you a whole bunch of options that you can play with on the fly by using the ```
synclient Paramater=somevalue
``` and you can set permantly in your xorg.conf file as i have done. There should be some options for the corners, Anyways play around with the options listed by synclient.

---

### Post by racyrefinedraj on 2007-06-14
Aha! that did it!

here's my new xorg.conf, for those interested

```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "RTCornerButton"        "0"
        Option          "RBCornerButton"        "0"
EndSection

```

Now I can scroll through code without pasting crap all over it. Brilliant!

---

