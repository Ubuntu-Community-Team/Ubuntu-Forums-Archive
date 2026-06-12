---
title: "problems after nvidia graphics install"
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by smommer on 2008-02-21
Hi,

im completely new to linux and am having a problem after installing the NVidia driver. as soon as it asks for a restart i get a blank screen when xserver starts up, also sometimes i can hear the drumming sound of the login screen but still get nothing on screen. when this is the case i try logging in with my user name and password and i get the login sound, so it seems like linux is running but nothing is appearing on the screen. Like many other posts on the forum i have a Geforce 7600 GS

```
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2)
```

I have tried installing the driver off the nvidia site and through envy, i have also tried modifying xorg.conf to say:

```

Section "Device"
Identifier	"Generic Video Card"
Driver		"nvidia"
BusID		"PCI:1:0:0"
EndSection
``` 

After trying the stuff ive seen in posts on similar topics in the forum im completely lost at what to try next, can anyone help?

my mother board is a chaintech ct-9pjl

my current xorg.conf is now, i had to change it back to get some kind of screen up:

```
Section "Files"
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
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Extensions"
EndSection
```

im a complete linux beginner so im still not familiar with many commands etc yet

---

### Post by overdrank on 2008-02-21
HI and have you tried the command ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by smommer on 2008-02-21
hi, thanks for the reply

I tried a fresh install, incase i screwed anything up with the old install, and installed nvidia-glx-new from the synaptic package manager. did the restart it asked for and got the blank screen, so booted in recovery mode and ran

```
dpkg-reconfigure -phigh xserver-xorg
```

and selected the nvidia driver, ran startx and got same problem, monitor just goes to no signal.

the only way i can seem to get a window up is to choose the vesa driver

---

### Post by uberlube on 2008-02-21
Use envy to install driver:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by smommer on 2008-02-21
i tried this on my previous insall but i'll give it a go again...

edit: tried installing envy and installing driver through that but same thing happens, monitor goes to no signal as x is starting. i tried running

```
dpkg-reconfigure -phigh xserver-xorg
```

again after the first restart specifying the nvidia driver but the same happens. I hope someone can help, this is really frustrating

---

### Post by julien-1993 on 2008-02-21
try without the -phigh

just 
```

sudo dpkg-reconfigure xserver-xorg
```

if you are at the blank screen and want to enter line command

ctrl-alt-F1 or ctrl-alt-F2

that way you dont need to reboot or anything to make multiple try

you may want to try with and without framebuffer.

choose only one lower resolution first and low refresh rate , you will fine tune later

also they ask at the begginning of sudo dpkg-reconfigure xserver-xorg to write the Files section, choose the default option,

 they ask a second time about writing some configuration....I dont remember what...try yes and no. 

The last time they ask about writing a configuration is the xorg.conf itself so say yes.

you can see any error produced by startx in /var/log/Xorg.0.log , it refer to the last attempt it did.

should help you...if it dosent work try with nvidia-glx but I dont guarentee anything with that.



edit: after installing nvidia-glx you must do
sudo nvidia-glx-enable
dont know the command for nvidia-glx-new, maybe its the same
but this is definitly required to enable the driver

---

