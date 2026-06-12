---
title: "Which driver for Intel Express Integrated Graphics Controller"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by jlhughes on 2007-04-21
SOLUTION AT END OF POST...

I did a fresh install of Feisty on a laptop with a display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller

I had previously been running Edgy without problems.

Everything works EXCEPT the screen resolution is stuck at default VGA 1024x768.

I have tried manually changing the resolution, but xorg reports that the driver installed doesn't support the 1280x800 resolution for this laptop.

What driver do I want to install?

Here's the relevant xorg.conf info:


Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "vbe"
EndSection


Section "Device"
Identifier "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
Driver "i810"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-64
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x800"
EndSubSection
EndSection
Edit/Delete Message

SOLUTION:

Open up a terminal and type in

> sudo apt-get install 915resolution


Reboot your machine and you will find your screen resolution option will have the higher option.

---

### Post by celticbhoy on 2007-05-04
Have tried the above with Intel express 82945G integrated graphics on a gigabyte motherboard with no success. I know it can run at 1280x800, as it does on dual boot with Vista.

only difference in xorg.conf is :-

Section "Device"
	Identifier	"Intel 829459 Express"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"  ### This line differs from above tutorial
EndSection

is the above line the prob. Dont want to delete it in-case it has a use.

any ideas welcome.

---

### Post by SpectralDesign on 2007-08-12
Did you ever get this working?  I got a Presario V6000 that I want to get running Ubuntu at 1280x800 (and get the Broadcom wlam up too....)

---

### Post by celticbhoy on 2007-08-12
Yeah, got it to 1280x800. Prob is I cant remeber how.

will give it some thought and post back when I remeber. Sorry.

---

### Post by jlhughes on 2007-08-12
Have you tried this:

> sudo apt-get install 915resolution

---

### Post by SpectralDesign on 2007-08-13
Yes, jhughes, that's what got it working for me!

There you go celticbhoy... mightnot be what did it for you, but it worked in my case!

Thanks!

---

