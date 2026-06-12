---
title: "Problem with screen resolution when using 2 external screens"
date: 2019-07-27
forum: Hardware
---

### Post by pethel on 2019-07-27
I have a problem with the resolution on one of the screens when using 2. 

This is my system

[ATTACH=CONFIG]283688[/ATTACH]

I have tried this. The option shows up in the list of resolutions but can not be applied.

```

xrandr --newmode "3840x2160_60.00"  712.75  3840 4160 4576 5312  2160 2163 2168 2237 -hsync +vsync
xrandr --addmode DP-1-1 3840x2160_60.00

```

For some reason my DELL screen is recognized as a Synaptics. Its not about the screen. If I just connect this as the only screen it works. 
[ATTACH=CONFIG]283689[/ATTACH]

Well I have tried everything I can think of. I believed xrandr could be my way out of this but apparently not.

---

### Post by Autodave on 2019-07-27
Some info on your equipment may help.  Also, what video card are you using?  Did you install a driver for it?  If so, what one and where did you get it from?

The screen that isn't working properly: how is it connected to the PC?

---

### Post by pethel on 2019-07-27
Video card I guess is on the screenshot:
Intel Kabylake GT2


I did not install any driver. My understanding is that it should already be part og Ubuntu when using Intel integrated card?


The broken one is HDMI from screen to HDMI into dock station. The screen is working. Just on some terrible resolutions.

---

