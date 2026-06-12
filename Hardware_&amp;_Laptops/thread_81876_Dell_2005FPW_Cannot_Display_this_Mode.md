---
title: "Dell 2005FPW Cannot Display this Mode"
date: 2005-10-25
forum: Hardware &amp; Laptops
---

### Post by RSX311 on 2005-10-25
I can boot up to Gnome just fine and the resolution is fine at 1680x1050 but when I Log out or Reboot and it goes to the Text screen to show it's logging off or rebooting  I get a black screen and my Monitor says "Cannot Display this mode"  This happend after I installed the ATI fglrx drivers.  Im thinking it's a refresh rate problem, but I don't know how to fix it, anybody have any ideas?

Thanks

---

### Post by mrtrick on 2005-10-25
I'm having the same problem with a Dell 1905FP. Any help would be appreciated.

---

### Post by Saarg on 2005-10-25
Have you edited your xorg.conf file to only use 60Hz refresh rate?
But I'm not sure if that would help since your problem is after the Xserver is closed. If I understood you correctly.
I have the same monitor and an ATI card with the fglrx driver installed. You installed through Synaptic or downloaded file from ATI homepage.

I'm at work right now so can't help much. I'll check when I get home.
I know I had to add the right modeline in xorg.conf for the monitor to work correctly. I can not remember if I had the same problem as you.
Could you post your xorg.conf file? It's in /etc/X11/

---

### Post by RSX311 on 2005-10-25
hmm, how do I make it only run 60hz?  I found some other threads with the correct modelines to use with our monitors but it doesn't seem to work. I also changed the horizsync and vertsync and that didn't work either. Maybe setting it to only run 60hz will work?  I installed fglrx from synaptic. Here's my xorg.conf

Thanks

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
#	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
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
	Identifier	"ATI Technologies, Inc. Radeon X800 XL (R430 UM)"
	Driver		"fglrx"
	BusID		"PCI:5:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	UseModes "16:10"
  	HorizSync 30.0 - 83.0
  	VertRefresh 56.0 - 75.0	

#	HorizSync	28-84
#	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X800 XL (R430 UM)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
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

Section "Modes"
  Identifier "16:10"
  ModeLine "1680x1050" 146.2 1680 1784 1968 2256 1050 1051 1054 1087 -hsync -vsync
EndSection

---

### Post by Saarg on 2005-10-25
To just have 60Hz refresh rate, remove 56 - 75 and replace with only 60.
In my modeline I have "1680x1050@60". 

I will compare it more when I finish work in about 2 hours.
You have no problem when changing to Console with ctrl+alt+F1?

---

### Post by RSX311 on 2005-10-25
I tried setting it 60hz only and that didn't work :(

I also tried going to the console with ctrl+alt+F1 and it said "Cannot display this Mode" again and I had to reboot to get back into gnome.

I appreciate your help

---

### Post by Saarg on 2005-10-26
It does not work to go back to Gnome with ctrl+alt+F7?
I don't think this problem is related to your xorg.conf because this only has the configuration for the Xserver and when you are in the console you don't use the Xserver. Correct me if I'm wrong.
What happens if you change the driver to "ati" instead of "fglrx" and restart the Xserver?(ctrl+alt+backspace)
I do not have the same modeline as you. Here is mine:
```
Modeline "1680x1050@60" 146.2 1680 1784 1960 2240 1050 1052 1058 1089 -hsync +vsync
```

Here is my complete xorg.conf
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"dbe"
SubSection "extmod"
	Option "omit xfree86-dga"
EndSubSection
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"no"
EndSection

#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"		"/dev/input/mice"
#	Option		"Protocol"		" ExplorerPS/2"
#	Option		"Buttons"		"8"
#	Option		"ZAxisMapping"		"4 5"
#EndSection

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver	"mouse"
	Option	"Protocol"	"evdev"
	Option	"Dev Name"	"Logitech USB-PS/2 Optical Mouse"
	Option	"Dev Phys"	"usb-*/input0"
	Option	"Device"		"/dev/input/event3"
	Option	"Buttons"	"8"
	Option	"ZAxisMapping"	"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X800 XT (R420 JP)"
#	Driver		"ati"
#	BusID		"PCI:1:0:0"
	Driver "fglrx"
	Option "UseInternalAGPGART" "no"
	Option "TVFormat" "NTSC-M"
    Option "TVStandard"                 "NTSC-M"
	Option "DesktopSetup" "single"
     	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	60
	Modeline "1680x1050@60" 146.2 1680 1784 1960 2240 1050 1052 1058 1089 -hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X800 XT (R420 JP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
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
```

You could try to add this to the kernel line in /boot/grub/menu.lst. On the end of that line. If you have to remove the "splash" I'm not sure.
```
vga=773
```

Hope some of this helps.

---

### Post by RSX311 on 2005-10-26
yeah, I think you're right about it not being related to the xorg.conf.  I'll try your modeline is see what happens.  I aslo found another issue when playing movies it's choppy and the images are getting torn horizontally.  Kind of like when playing FPS games and you have vertical sync off.  I think my refresh rate is all messed up :(

I can't startx with the "ati" as the driver, it just gives me "cannot start x."  So I had to choose "vesa" then install fglrx to get it working.  It works fine when I used vesa, it shows me the shutdown text when I leave Xserver.

---

### Post by RSX311 on 2005-10-26
nope, didn't work :(  thanks for your help, Im going to quit for tonight and try again tomorrow.

---

### Post by Saarg on 2005-10-26
Are you using Digital or Analog connection to your monitor?
If you write this in a console
```
fglrxinfo
```
What do you get?
If you shange your driver back to vesa and uninstal fglrx driver in synaptic and download the driver from ATI and install it that way. Is it the same? There is a new er version on ATI's site than in the repositories.
Since ctrl+alt+F* is working with vesa there has to be some problem with the driver I think.

---

### Post by RSX311 on 2005-10-26
First I tried the drivers in the repository and it didn't work, so I followed a how-to to install the 8.18.6 drivers and still have the same problem

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XL Generic
OpenGL version string: 1.3.5395 (X4.3.0-8.18.6)

---

### Post by Saarg on 2005-10-26
Sorry to hear that you still have the same problem. I have tried to reproduce your error here, but to no luck. If I find a solution I'll let you know.
I'm using Kubuntu. You are using Ubuntu? I'm not sure if that has anything to do with it though. I just finished customizing my install, so I doubt I'll install Ubuntu just to check if I get the same error.

I hope someone else is able to help you solve your problem.

---

### Post by RSX311 on 2005-10-27
yeah Im running ubuntu for amd64, maybe thats my problem, hehe.  Thanks for all your help, I hope I'll figure it out.

---

### Post by Jim Z on 2005-12-09
Well, I'm having the same issue here, using the i386 release of Breezy.

Dell 2005FPW
ATi Radeon X800XL (PCI Express) connected to the monitor via DVI
Athlon 64 processor
"fglrx" driver installed via Synaptic

I did the modeline changes required to get 1680x1050, but this problem occurs no matter what the desktop resolution is set to.  Any time I go to log out, restart, or anything that stops X, I get the "DVI-D: Cannot Display This Mode" error on the screen and can only recover with a hard reset.

I have not checked it with the "radeon" driver yet, so I'll test that tonight.

---

### Post by RSX311 on 2005-12-09
[QUOTE=Jim Z]Well, I'm having the same issue here, using the i386 release of Breezy.

Dell 2005FPW
ATi Radeon X800XL (PCI Express) connected to the monitor via DVI
Athlon 64 processor
"fglrx" driver installed via Synaptic

I did the modeline changes required to get 1680x1050, but this problem occurs no matter what the desktop resolution is set to.  Any time I go to log out, restart, or anything that stops X, I get the "DVI-D: Cannot Display This Mode" error on the screen and can only recover with a hard reset.

I have not checked it with the "radeon" driver yet, so I'll test that tonight.[/QUOTE]

I haven't been able to figure it out yet :(  Actually one time it did show the shutdown process and surprised me, but it wouldn't do it again after that, weird...

---

### Post by Jim Z on 2005-12-10
well, I switched it to the "radeon" driver and I don't have the problem anymore.  So I guess it's something with fglrx.

---

