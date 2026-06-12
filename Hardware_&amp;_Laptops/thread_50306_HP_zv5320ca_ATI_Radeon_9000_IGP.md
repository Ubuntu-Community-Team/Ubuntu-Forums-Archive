---
title: "HP zv5320ca ATI Radeon 9000 IGP"
date: 2005-07-19
forum: Hardware &amp; Laptops
---

### Post by kylenewton on 2005-07-19
Heya, been working on this all day and haven't had any luck with installing the fglrx and getting my ati working with fgl_glxgears or glxgears.

I've tried following the tutorials on the boards here, but they seem to be for version 8.12, wheres 8.14 is the most recent version I can find. And even in following the 8.12 version with my 8.14 script from the ATI site, still no good.

I've exhausted most any combination of things to do and have had no luck, so I'm not posting all the various combinations I've completed. Rather, I'd appreciate if anyone has been able to get some generic ATI drivers working with their LAPTOP (and not a desktop system, I'm looking for drivers that work with a laptop if it makes a difference), could you be so kind as to point a guy in the right direction?

When I have my system at a stable point where it will run glxgears without locking up I get at most ~250 fps

fglrxinfo gives me >>
OpenGL renderer string: MOBILITY RADEON 9000/9100 IGP Series DDR Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

Thanks for your help.

[edit]

Here's what I do, for the record.

I download the .run file from the ATI web site.

sudo sh ./ati-blahblah

it installs fine with an automatic/default settings

I then, as per the instructions on another tutorial in this forum, check to make sure my /etc/X11/xorg.conf is to suit.

I'm using Kubuntu, is this where I may be going wrong? Should I be editing XFREE86-Conf4 instead?

At this point, a reboot should work, at least according to the other tutorial. No luck. And when I run glxgears I get 

error: DDX driver parameter mismatch: got 704 bytes, but expected 832 bytes.
libGL error: InitDriver failed

Followed by my dismally low fps from glxgears.

---

### Post by s_p_a_r_k_y on 2005-07-20
You should post your xorg conf file. Also make sure that the fglrx kernel module is loaded

```
lsmod | grep fglrx
``` 
if no lines are returned its not loaded. Stick it in /etc/modules so it gets loaded when you boot and to try it out now, sudo modprobe fgrlx

Also check the /var/log/Xorg.0.log file for lines saying dri is off. I just
```
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```
is what I get but the lines above it will tell you why. I have the composite extension on so dri doesn't work with that but thats my choice. disable composite.

---

### Post by TheSavage on 2005-07-20
You've got the driver working without 3D optimization.  ATI, at this time, doesn't have a driver out there that support 3D for their line of 9100 IGP.  If you activate the DRI to get the 3D, you'll end up with lock up when you start fgl_glxgears or glxgears.

Here's a quote from ATI
> Caution:
This software driver provides 2D support only for the ATI Radeon® 9100 IGP and ATI Radeon® 9100 PRO IGP.

I've done a lots of reseach myself about it, before I find that line from the installer instruction on their site.  I can only look forward for them to start provinding 3D for 9100IGP product.

---

### Post by kylenewton on 2005-07-20
I'm at work at the moment, so I haven't had an opportunity to try anything else out. But judging by that last post, I've possibly done everything correctly? The problem being I won't ever have 3D support with my 9000 IGP with the 8.14.13 drivers? I'll try the first suggestion when I get off work, anyway. I'll post back when I know what happens.

---

### Post by kylenewton on 2005-07-20
My xorg.conf file as follows:
```

#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
	Driver		"fglrx"
	Option		"UseInternalAGPGART"	"no"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

```
> lsmod | grep fglrx
fglrx                 229568  0
```
So that's all good, it's loaded in the modules.

Here's the bit from my /var/log/Xorg.0.log
```
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```

And finally, when I run fgl_glxgears it doesn't lock up, thankfully. Here's the console output:
```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  145 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  32
  Current serial number in output stream:  32
```

I suppose I'll never have 3D support with these ATI drivers, but thanks for the help.

---

### Post by s_p_a_r_k_y on 2005-07-21
what are the lines right above the
"
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available    "

THose are the lines which usually tell you why DRI failed

---

### Post by th2 on 2006-01-31
Not to worry.  I have asked ATI why their drivers do not support 3D on Radeon 9000 IGP?

---

