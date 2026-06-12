---
title: "Toshiba Synaptics Touchpad “Frame Rate” Issue"
date: 2015-04-11
forum: Hardware
---

### Post by john_g3 on 2015-04-11
Hi,

I'm trying to fix the Synaptics touchpad on my Toshiba Satellite S855D-00U with Ubuntu 14.04 freshly installed.

When I use the touchpad, the mouse cursor seems to move at a low "frame rate", but this issue is not present with an external mouse. For example, if I drag a window with the touchpad, the cursor and the window will move at a low "frame rate" (it's laggy), but if I switch to a mouse, everything is fluid. This issue is not present on Windows 8.1. I tried to record a video of the problem, but it didn't work out well.

Here's all the things I tried that didn't work:

[LIST]
[*]I tried to change the touchpad preferences in Ubuntu settings
[*]I tried different configurations with *synclient*
[*]I added *i8042.nomux=1* to the boot line
[*]I updated my BIOS
[*]I updated the system to the latest kernel
[*]The problem also occurs on Ubuntu GNOME and Kubuntu
[/LIST]
Here's the model information I could find with a *dmesg*:
```
[    2.563772] psmouse serio1: synaptics: queried max coordinates: x [..5634], y [..4598]
[    2.614110] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400, board id: 1680, fw id: 706145
[    2.614123] psmouse serio1: synaptics: Toshiba Satellite S855D detected, limiting rate to 40pps.
[    2.648350] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
```

and a *cat /proc/bus/input/devices*:
```
I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input5
U: Uniq=
H: Handlers=mouse0 event4 
B: PROP=9
B: EV=b
B: KEY=6420 30000 0 0 0 0
B: ABS=260800011000003
```

Does anyone have an idea on how to fix this? Thank you!

---

### Post by john_g3 on 2015-04-15
Bump

---

