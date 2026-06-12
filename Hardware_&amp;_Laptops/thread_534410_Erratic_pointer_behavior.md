---
title: "Erratic pointer behavior"
date: 2007-08-25
forum: Hardware &amp; Laptops
---

### Post by skyemoor on 2007-08-25
The cursor/pointer suddenly zips off to one side (or corner) just to zip to another side moments later. It started out only doing this for a few seconds, gradually increasing to minutes now, making this laptop virtually unuseable.

I undocked the laptop and started using the touchpad. The problem seemed to go away, thought it has started again. I'm wondering if it has anything to do with the temperature, because it only seems to do this after it has warmed up and the fan starts coming on longer intervals.  I had a hard time submitting this post.

Dell Latitude C810
Feisty 7.04

# This file is automatically updated on xserver-xorg package upgrades *only* 
# if it has not been modified since the last upgrade of the xserver-xorg 
# package. 
# 
# If you have edited this file but would like it to be automatically updated 
# again, run the following command: 
#   sudo dpkg-reconfigure -phigh xserver-xorg 

Section "Files" 
	Fontpath	"/usr/share/fonts/X11/misc" 
	Fontpath	"/usr/share/fonts/X11/cyrillic" 
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled" 
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled" 
	Fontpath	"/usr/share/fonts/X11/Type1" 
	Fontpath	"/usr/share/fonts/X11/100dpi" 
	Fontpath	"/usr/share/fonts/X11/75dpi" 
	# path to defoma fonts 
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" 
EndSection 

Section "Module" 
	Load		"i2c" 
	Load		"bitmap" 
	Load		"ddc" 
	Load		"extmod" 
	Load		"freetype" 
	Load		"glx" 
	Load		"int10" 
	Load		"vbe" 
EndSection 

Section "InputDevice" 
	Identifier	"Generic Keyboard" 
	Driver		"kbd" 
	Option		"CoreKeyboard" 
	Option		"XkbRules"	"xorg" 
	Option		"XkbModel"	"pc105" 
	Option		"XkbLayout"	"us" 
EndSection 

Section "InputDevice" 
	Identifier	"Configured Mouse" 
	Driver		"mouse" 
	Option		"CorePointer" 
	Option		"Device"	"/dev/input/mice" 
	Option		"Protocol"	"ImPS/2" 
	Option		"ZAxisMapping"	"4 5" 
	Option		"Emulate3Buttons"	"true" 
EndSection 

Section "InputDevice" 
	Driver		"wacom" 
	Identifier	"stylus" 
	Option		"Device"	"/dev/input/wacom" 
	Option		"Type"	"stylus" 
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY 
EndSection 

Section "InputDevice" 
	Driver		"wacom" 
	Identifier	"eraser" 
	Option		"Device"	"/dev/input/wacom" 
	Option		"Type"	"eraser" 
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY 
EndSection 

Section "InputDevice" 
	Driver		"wacom" 
	Identifier	"cursor" 
	Option		"Device"	"/dev/input/wacom" 
	Option		"Type"	"cursor" 
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY 
EndSection 

Section "Device" 
	Identifier	"nVidia Corporation NV11 [GeForce2 Go]" 
	Driver		"nvidia" 
	Busid		"PCI:1:0:0" 
	Option		"AddARGBVisuals"	"True" 
	Option		"AddARGBGLXVisuals"	"True" 
	Option		"NoLogo"	"True" 
EndSection 

Section "Monitor" 
	Identifier	"HC194D" 
	Option		"DPMS" 
EndSection 

Section "Screen" 
	Identifier	"Default Screen" 
	Device		"nVidia Corporation NV11 [GeForce2 Go]" 
	Monitor		"HC194D" 
	Defaultdepth	24 
	SubSection "Display" 
		Depth	1 
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x640"	"640x480"	"640x400" 
	EndSubSection 
	SubSection "Display" 
		Depth	4 
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x640"	"640x480"	"640x400" 
	EndSubSection 
	SubSection "Display" 
		Depth	8 
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x640"	"640x480"	"640x400" 
	EndSubSection 
	SubSection "Display" 
		Depth	15 
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x640"	"640x480"	"640x400" 
	EndSubSection 
	SubSection "Display" 
		Depth	16 
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x640"	"640x480"	"640x400" 
	EndSubSection 
	SubSection "Display" 
		Depth	24 
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x640"	"640x480"	"640x400" 
	EndSubSection 
EndSection 

Section "ServerLayout" 
	Identifier	"Default Layout" 
  screen "Default Screen" 
	Inputdevice	"Generic Keyboard" 
	Inputdevice	"Configured Mouse" 
	Inputdevice	"stylus"	"SendCoreEvents" 
	Inputdevice	"cursor"	"SendCoreEvents" 
	Inputdevice	"eraser"	"SendCoreEvents" 
EndSection 

Section "DRI" 
	Mode	0666 
EndSection

__________________

---

### Post by skyemoor on 2007-10-28
I finally figured out that disconnecting the trackpointer would solve the problem, after seeing examples from others.

The Dell service guide online shows how to remove the keyboard.
[http://support.dell.com/support/edocs/systems/latc810/en/sm/2e40520.htm#999019](http://support.dell.com/support/edocs/systems/latc810/en/sm/2e40520.htm#999019)

Simply snip the smaller tape (silver) from the keyboard and reassemble.  Your done.

---

