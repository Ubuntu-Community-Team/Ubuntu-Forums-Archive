---
title: "Radeon HD 5850"
date: 2011-07-10
forum: Hardware
---

### Post by Gnorrogh on 2011-07-10
Hey guys!

I'm getting really frustrated here, been trying for almost a full day to get my driver working correctly, but I just can't seem to get it working. I've been following dozens of guides and tutorials, official and unofficial, but no luck so far.

I'm using Gnome 3, not that that would make such a big difference?

The icons in the top are twisted, overall graphics performance slow, wrong colors in weird places, description texts are italic, for some reason, among other things.

What I have in xorg.conf:

> Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:5:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


Using the proprietary driver that comes with Ubuntu 11.04.

Any help would be greatly appreciated.

---

### Post by Gnorrogh on 2011-07-11
I'm sorry for the bump, but anyone?

---

### Post by mastablasta on 2011-07-11
Gnome 3? Gnome 3 is not compatible with Unity yet. This could be the reason why you are experiencign the problems. Do you maybe mean Gnome classic interface?
 
Have you tried any other DE? Like for example KDE or XFCE? DO they give u the same issues?

---

### Post by Gnorrogh on 2011-07-11
> **mastablasta said:**
> Gnome 3? Gnome 3 is not compatible with Unity yet. This could be the reason why you are experiencign the problems. Do you maybe mean Gnome classic interface?
 
Have you tried any other DE? Like for example KDE or XFCE? DO they give u the same issues?

No, I mean Gnome 3. I'm using Gnome 3 on 2 other computers here at home as well, and they're both working fine. I'm using the UGR ppa. Unity does look a little better, but still the same poor performance and graphics glitches.

---

### Post by Gnorrogh on 2011-07-12
No one? I guess I'll have to uninstall again, then.

---

