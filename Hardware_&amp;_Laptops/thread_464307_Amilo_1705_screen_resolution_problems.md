---
title: "Amilo 1705 screen resolution problems"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by teb on 2007-06-04
Dear all,

I have installed Ubuntu Feisty Fawn on a new Fujitsu Siemens Amilo Li 1705. Most went smooth but the screen resolution sticks to 800x600. The only options in the "screen resolution" menu are this one and the 640x800.

I dived in the forums to find a solution. 
sudo xresprobe siliconmotion
id: 
res: 
freq: 
disptype: lcd/lvds

sudo ddcprobe | grep monitorrange gives me nothing.
editing xorg.conf by including the 1200x800 resolution doesnt change anything (nor after restart of gdm)
also have i tried to add in the xorg.conf some data for horizontal sync etc but that makes it impossible to read the screen.

Right now it is using the vesa driver. I have no clue if this is right or that i should use another. 

You see I am lost :(

Maybe someone can point me in the right direction. Heres my xorg, or part of it:


Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
	Depth           1
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x800" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x800" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by hkahwaji on 2007-06-06
Hi,

Use the below instructions if you have an ATI video card. Mine is X1400

I had the same issue and I was able to install the following driver for my ATI Radeon X1400 card. Open a terminal and run the following commands:

sudo apt-get install xorg-driver-fglrx
sudo depmod –a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv


Restart the system and then go to screen resolution settings to change the resolution.

---

