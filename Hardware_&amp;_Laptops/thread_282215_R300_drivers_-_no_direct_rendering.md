---
title: "R300 drivers - no direct rendering"
date: 2006-10-22
forum: Hardware &amp; Laptops
---

### Post by chaosgeisterchen on 2006-10-22
Hi folks,

I installed the R300-drivers (**xserver-xorg-driver-ati**) and the referring packages in order to use DRI but when I type in **glxinfo** I get that:
```
chaosgeisterchen@sequentia:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2

```

followed by module descriptions, as usual. So, the question is how to get direct rendering to work, if I may ask you for help :) The forums search did not help me so far, so I am sorry to have posted a duplicate of an already solved issue.

Thanks in advance.

cg

---

### Post by William the Conquerer on 2006-10-22
well, are ya sure direct rendering will work with your graphics card?

also, in a terminal window type this ```
$ lsmod |grep radeon
``` and you SHOULD see something about radeon.  you could also do something like ```
$ dmesg |grep radeon
``` and that should also display something about radeon...  ok, so if both of those don't give any output open your /etc/modules file ```
$ sudo nano /etc/modules
``` and add the line "radeon" to the end of it (you don't need the quotes)

I'm not even sure that you have to have this, but...  I do and I have direct rendering working.  What does your /etc/X11/xorg.conf file look like?

---

### Post by chaosgeisterchen on 2006-10-22
Thanks for the reply. My xorg.conf is not very spectacular, but these should be the pieces of information really interesting concerning graphics:

```

...
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
EndSection
...
Section "Device"
	Identifier	"ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
	Driver		"radeon"
	Option "DRI" "true"
	 Option "ColorTiling" "on"
	 Option "EnablePageFlip" "true"
	 Option "AccelMethod" "XAA"
	 Option "XAANoOffscreenPixmaps"
	 Option "RenderAccel" "true"
	Option "AGPFastWrite" "on" 
	Option "AccelDFS" "1"
	BusID		"PCI:5:0:0"
EndSection
...
```

I really assume that a X300 is capable of direct rendering.. otherwise I would not have been able to run XGL back then (it was slow as hell).

---

### Post by benjou on 2006-10-25
I have a mobility X300 working with radeon drivers with SOME dri
At least:
```
benoit@laptop-benoit:~$ glxinfo |grep rendering
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes

```

I still have problem for google-earth (slow as hell) and kiba-dock (not transparent)

Here is my modules and device section:
```
Section "Module"

####
####
	Load  "i2c"
	Load  "bitmap"
    		Load	"dbe"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection
```

```
Section "Device"
	#Option		"UseFBDev"		"true"
	#Option       	"UseInternalAGPGART" "no"
	#Option       	"KernelModuleParm" "agplock=0"
	Identifier  "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver      "radeon"
	BusID       "PCI:1:0:0"
    Option 		"AccelMethod" "XAA" # Use XFree86 Acceleration Architecture
    Option 		"XaaNoOffscreenPixmaps" "false" # Faster RENDER acceleration
    Option 		"RenderAccel" "true" # Enable the hardware render acceleration

    Option	  	"VideoOverlay" "on"
    Option	  	"OpenGLOverlay" "off"
    Option 		"DPMS"
EndSection

```

---

### Post by chaosgeisterchen on 2006-10-27
It works now.. the problem was that XOrg 7.0 did not support the direct rendering for R300 drivers it seems.

It now works (but with several freezes)

---

### Post by fuoco on 2006-10-27
I have "direct rendering: yes" in glxinfo, but still when I use for example glxgears i get 100% cpu and about 25-30fps. 
This was true in dapper and still is in edgy. Any idea what is the problem ?

---

### Post by fuoco on 2006-12-17
I used 'prevu' to install newer mesa packages with a more recent r300 driver. This has resulted in my glxgears raising from 25 to 900. But now planet penguin racer has only 2.5 fps. Any idea?

---

