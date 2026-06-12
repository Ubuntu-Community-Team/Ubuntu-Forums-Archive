---
title: "Touchpad Scrolling Issues On Laptop"
date: 2007-02-15
forum: Hardware &amp; Laptops
---

### Post by Keymaster on 2007-02-15
On my laptop (Sony VAIO VGN-FE550G) my the right side of my touchpad (Synaptics touchpad) acts as a scrolling feature in Ubuntu 6.06. It is driving me nuts, and interfering with my work so I was wondering if anyone knew how to turn off the scrolling. There was nothing for it in the Mouse settings under Preferences. Any help would be greatly appreciated. Thanks.

---

### Post by reacocard on 2007-02-15
> **Keymaster said:**
> On my laptop (Sony VAIO VGN-FE550G) my the right side of my touchpad (Synaptics touchpad) acts as a scrolling feature in Ubuntu 6.06. It is driving me nuts, and interfering with my work so I was wondering if anyone knew how to turn off the scrolling. There was nothing for it in the Mouse settings under Preferences. Any help would be greatly appreciated. Thanks.

Open a terminal (Applications->Accessories->Terminal) and copy in the following, then hit enter:
```
gksudo gedit /etc/X11/xorg.conf
```
Now find the section that starts with
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
```
Add this line inside that section:
```
	Option		"VertEdgeScroll"	"0"
```
Save the file, then reboot. Side scroll will be disabled.

---

### Post by Keymaster on 2007-02-15
Thanks, but when I tried that it didn't work.  It gave me the idea of looking at my xorg.conf file, and I noticed that there was an entry for
```
Option         "HorizScrollDelta"    "0"
```
so I tried
```
Option         "VertScrollDelta"    "0"
```
and that worked, so thanks for the inspiration.

---

