---
title: "Wrong resolution for LaCie monitor"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by Neotonian on 2008-01-08
My Gutsy 7.10 is offering only a screen resolution of 800x600 or 640x480, at 60 or 56 Hz. 

I have a LaCie 22inch `electron blue IV' monitor, a high-end CRT bought just before CRTs ceased being standard. (Some regard it as a dinosaur, but it's excellent for someone with poor sight.)

When I bought my box, in September, it picked up a suitable resolution, probably about 1280x1024, but  I was forced to do a reinstall this week. Possibly relevant: the box came with FF 7.04 which I upgraded to 7.10 in December. That kept the good resolution, but the reinstall this week was after several formats and repartitioning, to clear errors. 

Under `Screens and Graphics Preferences' I see just `Generic: Plug n Play' for the screen but the correct `nVidia Riva 128 , Riva TNT, GeForce 6 Series' for the card. 

The screen menu does not list any LaCie monitors at all and there doesn't seem to be anything about them on the forums either. 

I'm new to Ubuntu, a genuine convert after years of RH and FC. I don't have to have exactly 1280x1024 but something close to it. 

Neot

---

### Post by Neotonian on 2008-01-08
I should add, from /etc/X11/xorg.conf :

>>>>>

Section "Device"
	Identifier	"nVidia Corporation C51PV [GeForce 6150]"
	Driver		"nv"
	BusID		"PCI:0:5:0"
EndSection

Section "Monitor"
	Identifier	"electr22b4"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation C51PV [GeForce 6150]"
	Monitor		"electr22b4"
	DefaultDepth	24
	SubSection "Display"
		Modes		"2048x1536" "1920x1440" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

<<<<<

So xorg is picking up the monitor but not treating it correctly. I tried deleting the low resolutions under Screen, but that did not help. 

Hope you can point me in the right direction ...

N

---

### Post by taurus on 2008-01-08
Or reconfigure your X server again with

Applications -> Accessories -> Terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
When it's done, either reboot or restart X with <Ctrl><Alt>Backspace.

---

### Post by Neotonian on 2008-01-08
Thanks Taurus. I did that but it hasn't changed anything. The parts of the /etc/X11/xorg.conf file which I quoted previously are still the same and the resolution is the same (after reboot). 

The operation did change XkbLayout from us to gb, so it definitely took place. 

I'm completely puzzled. 

N

---

