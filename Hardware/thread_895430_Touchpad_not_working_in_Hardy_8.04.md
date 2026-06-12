---
title: "Touchpad not working in Hardy 8.04"
date: 2008-08-20
forum: Hardware
---

### Post by theirishkiwi on 2008-08-20
Ok, so Have installed Hardy 8.04 on a Medion MAM2010 laptop with success. This is my first foray into Linux and impressed so far but for a few minor but still frustrating issues.

- Touchpad has never worked
- Battery does not show % remaining

So, the Touchpad. I have read extensively and tried a number of the fixes talked about in various forums not just this one. 

So here what I have in  /proc/bus/input/devices

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3


and /etc/X11/xorg.conf
  
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"SHMConfig"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"
EndSection

I have also been trying but to no avail to get Gsynaptics to run hence the "SHMConfig" so help would be gratefully received there also.

Please help, I'm liking Ubuntu so far and this would much improve my experience.

Regards

Chris

---

### Post by theirishkiwi on 2008-08-21
*Bump*

---

### Post by leeko on 2008-09-03
Hi,

My wife has this same laptop, and I'd like to ubuntize it if possible. 

I'm hoping someone out there can help with this problem, which I also found when I ran the live CD of ubuntu  8.04.

Thanks in advance,

Lee Alkureishi

---

### Post by theirishkiwi on 2008-09-03
As much as the touchpad does not work and the battery fails to give you any information about how much charge remains when not plugged in, the laptop runs Ubuntu 8.04 fine. A little more Ram would be preferable but as long as you don't try and do too many things at once it's happy.

---

### Post by leeko on 2008-09-03
I understand. For me, it would be fine, but the lack of the touchpad kills the deal for my wife... She's never used linux before, and I'm trying to to convince her of the benefits of FOSS. Not having a touchpad isn't exactly a benefit!

Thanks,

Lee

---

