---
title: "Disabling Touchpad"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by Elanzer on 2007-03-13
Hello, using xubuntu edgy here. I'm having a problem disabling the synaptics touchpad on my Compaq Evo N600C laptop. The laptop has both a touchpad and tracking knob, and I don't ever use the touchpad, it tends to get in the way when I'm typing and I accidentally touch it. There's 2 sets of buttons, left/right click meant for the knob above the touchpad, and left/right click below the touchpad for touchpad use.

When I set ```
Option	"SendCoreEvents"	"false"
``` in xorg.conf, it disables the touchpad and leaves the knob functioning, but it also disables *both* sets of buttons, leaving the knob relatively useless because I can't click.

Normally on XP having the touchpad set to disabled in the bios leaves both sets of buttons functioning with touchpad disabled, but it seems xubuntu is ignoring the bios and enables the touchpad anyways.

Any help with this issue would be appreciated.

---

### Post by xyz on 2007-03-13
Hi,
See this : [Disabling Touchpad]("http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/")
And just to make sure, you saw this one:
[SynapticsTouchpad]("https://help.ubuntu.com/community/SynapticsTouchpad")
Just a thought:
Is it really a good idea? Say some day your mouse dies...you might need it! Just a thought.

---

### Post by Elanzer on 2007-03-13
You misunderstand, I only want the touchpad disabled so I can use the "eraser knob" and it's set of buttons, my laptop has both methods for cursor control.

The methods you posted I have tried already and give the same result as I mentioned in my opening post: It disables all sets of buttons and not just the touchpad, forcing me to either have the touchpad enabled (getting in the way) or force use of an external mouse.

I am looking for a way to disable the touchpad, without disabling all of the left/right click buttons like I have in Windows XP.

Now that I think about it, would it be possible to just set it's sensitivity to a nil value? Leaving it enabled but making it impossible to move the cursor with it

---

### Post by Elanzer on 2007-03-13
Yeah that did it. I set the sensitivity to zero and disable tap-clicking on the touchpad and got to retain my buttons for the other pointer without disabling it.

in xorg.conf:

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
**	Option		"MaxTapTime"		"0"**
**	Option		"MaxSpeed"		"0"**
EndSection
```

This effectively disables the touchpad from working without having to disable the hardware, that way I get to keep my buttons too.

Case closed

---

### Post by TheWizzard on 2007-03-13
> **Elanzer said:**
> You misunderstand, I only want the touchpad disabled so I can use the "eraser knob" and it's set of buttons, my laptop has both methods for cursor control.

The methods you posted I have tried already and give the same result as I mentioned in my opening post: It disables all sets of buttons and not just the touchpad, forcing me to either have the touchpad enabled (getting in the way) or force use of an external mouse.

I am looking for a way to disable the touchpad, without disabling all of the left/right click buttons like I have in Windows XP.

Now that I think about it, would it be possible to just set it's sensitivity to a nil value? Leaving it enabled but making it impossible to move the cursor with it

use qsynaptics

---

### Post by Cloudy on 2007-03-13
I followed the instructions on [http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/](http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/) and added the 

```

   Option          "SHMConfig"    "on"

```

line, but whenever I try to run the command to turn the touchpad off it asks me if SHMConfig is disabled.. even though I have it set to "on". I have a Synaptics Touchpad and I'm using Ubuntu 6.10 on a Dell Latitude C640, if it helps to know.

---

