---
title: "No acceleration on Intel 945GME"
date: 2008-12-28
forum: Hardware
---

### Post by pteri498 on 2008-12-28
I just got my EEE 900HA and installed Ubuntu 8.04 on it, plus the kernel modifications and some scripts to get the Webcam and Fn keys working.

The only issue now is my video card. lspci has the following output:
```

lspci | grep raphics
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

```

When I run **displayconfig-gtk**, it shows me that I am using the vesa driver, which is probably why I can't watch 3D ants crawling about at more than 0 FPS.

My /etc/X11/xorg.conf file is very generic and does not list anything in particular about my video.

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

```

I think I need to be using the Intel driver in displayconfig-gtk, but whenever I try, it reverts to vesa.

I'm wondering what driver I should be using, or what I should do to get full video support/acceleration for this system. Any ideas?

Thanks.

---

### Post by igknighted on 2008-12-28
Can you post the output of the command 'glxinfo | grep OpenGL'?

---

### Post by pteri498 on 2008-12-28
> **igknighted said:**
> Can you post the output of the command 'glxinfo | grep OpenGL'?

Sure, here it is:

```

$ glxinfo | grep OpenGL
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GME 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:

```

Might this be related to why Ubuntu is only using the Vesa driver?

---

### Post by igknighted on 2008-12-28
> **pteri498 said:**
> Sure, here it is:

```

$ glxinfo | grep OpenGL
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GME 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:

```

Might this be related to why Ubuntu is only using the Vesa driver?

Actually, that seems to indicate that 3d is working fine, and that you are using the intel driver.  If you really want to be sure, in the section "Device" in xorg.conf add a line that looks like this:
```
Driver "intel"
``` and log in/out.

What makes you think the driver isn't working (ie, any error messages)?

---

### Post by igknighted on 2008-12-28
When I use the intel driver, this is what I get from that command:
```
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset 20061102
OpenGL version string: 1.4 Mesa 7.2
OpenGL extensions:
```

When I use vesa, this is what I get:
```
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.2
OpenGL shading language version string: 1.10
OpenGL extensions:
```

You are almost certainly using the intel driver with 3d.  Performance may be poor, but it should work.

---

### Post by sam1948 on 2009-09-16
after connecting an external screen i had the same problem
this solved my problem:
-disconnect the external screen
-go to System-->Preferences-->resolution

make sure u only have there one screen

backup /etc/X11/xorg.conf
and copy the following parts instead of the existing one in 
/etc/X11/xorg.conf

I would even recommend to change the whole xorg.conf content with the following content

goodluck

```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2048 768
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection


```

---

### Post by stmiller on 2009-09-16
Please note: this thread is from 2008. A lot has changed with Intel graphics since then. Check out this wikipage:

[https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting)

---

