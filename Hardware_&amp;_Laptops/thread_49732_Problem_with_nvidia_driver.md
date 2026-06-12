---
title: "Problem with nvidia driver"
date: 2005-07-17
forum: Hardware &amp; Laptops
---

### Post by g7yh7uj8k on 2005-07-17
I am able to use th "nv" driver with no problems but when i change it to the driver "nvidia" xorg crashes. I have had no problem with this on other systems with the same card. here is my xorg.conf 

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

Section "Device"
	Identifier	"NVIDIA Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]"
	Driver		"nv"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"COMPAQ P75"
	Option		"DPMS"
        HorizSync    30-85
        VertRefresh  75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]"
	Monitor		"COMPAQ P75"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection


and here is the end part with the error from Xorg.0.log


(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0xF0000000
(--) NVIDIA(0): MMIO registers at 0xEE000000
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found


could thid be because i am using a diffrent kernel "k7 smp" on this system? or somthing else?   thanks dave

---

### Post by parabolize on 2005-07-17
Your xorg.conf looks OK to me but I am no expert. What nvidia driver you using? 7174 from your repositories or 7667 from nvidia.com? With 7667 there is a special driver for older cards. I think [this](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7667/NVIDIA-Linux-x86-1.0-7667-pkg0.run)  is the special driver.

---

### Post by farfargoth on 2005-07-17
[QUOTE=g7yh7uj8k]I am able to use th "nv" driver with no problems but when i change it to the driver "nvidia" xorg crashes. I have had no problem with this on other systems with the same card. here is my xorg.conf 

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

Section "Device"
	Identifier	"NVIDIA Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]"
	Driver		"nv"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"COMPAQ P75"
	Option		"DPMS"
        HorizSync    30-85
        VertRefresh  75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]"
	Monitor		"COMPAQ P75"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection


and here is the end part with the error from Xorg.0.log


(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0xF0000000
(--) NVIDIA(0): MMIO registers at 0xEE000000
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found


could thid be because i am using a diffrent kernel "k7 smp" on this system? or somthing else?   thanks dave[/QUOTE]
 you have to install the nvidia drivers... 
if you have a custom kernel: download the drivers, compile and run x.. should work... 

if you're using the one provided by ubuntu: apt-get nvidia-glx from a debian repository

---

### Post by fig_jam_uk on 2005-07-17
yes you need to use synaptic or kynaptic and download all nvidia packages ie nvidia-glx etc

---

### Post by g7yh7uj8k on 2005-07-17
sorry i didn't mention this eariler. I did install nvidia the packages,
from the repositories, nvidia-glx 1.0.7174.
The kernel I installed also was from the repositories linux-image-2.6.10-5-k7-smp.

---

### Post by parabolize on 2005-07-18
I think you may need to remove Load  "dri" from your xorg.conf. Here is what the [nvidia readme](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7174/README.txt)  says:

> If you already have an X config file working with a different driver
(such as the 'nv' or 'vesa' driver), then all you need to do is find
the relevant Device section and replace the line:

        Driver "nv"
    (or Driver "vesa")

with 

        Driver "nvidia"  

In the Module section, make sure you have:

        Load   "glx"

You should also remove the following lines:
      
        Load  "dri"
        Load  "GLcore"

Also change your VertRefresh to 50-150.

---

### Post by g7yh7uj8k on 2005-07-18
ok i removed  Load "dri"
It still will not start when using the nvidia driver.

---

### Post by g7yh7uj8k on 2005-07-18
After my last post I shutdown and rebooted whith the generic i386 kernel, and the driver loads up with no problems. So it is the k7 smp kernel that is causing the problem. Is there any way to fix this without recompiling the kernel? 

thanks dave

---

### Post by mo_x on 2005-07-18
Boot with the 2.6.10-5-k7-smp kernel and reinstall the nvidia-glx package.

---

### Post by g7yh7uj8k on 2005-07-18
ok it works now. When I installed the driver it installed linux-restricted-modules-2.6.10-5-386 but not linux-restricted-modules-2.6.10-5-k7-smp

thanks for the help dave

---

### Post by parabolize on 2005-07-18
[QUOTE=g7yh7uj8k]ok i removed  Load "dri"
It still will not start when using the nvidia driver.[/QUOTE]
Did you also change your VertRefresh to 50-150? Sorry I put it at the bottom of my post. You *need* to change this.

---

### Post by theToolman on 2005-08-28
This seems to be a problem with the binary nvidia driver and the optimised (k7 plus maybe others) kernels:  [http://www.ubuntuforums.org/showthread.php?p=321813#post321813](http://www.ubuntuforums.org/showthread.php?p=321813#post321813)

---

