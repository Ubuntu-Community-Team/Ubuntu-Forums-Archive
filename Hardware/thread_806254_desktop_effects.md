---
title: "desktop effects?"
date: 2008-05-24
forum: Hardware
---

### Post by 2j4ez on 2008-05-24
Hello I am now using ubuntu on my IBM thinkpad r40e all previous versions on ubuntu have not worked very well (keyboard problems)

Anyway i tried madriva linux on my laptop had the same problem with the keyboard 

On madriva linux i could do the desktop effects rotating cube,wobbly windows but i cannot get them to work in ubuntu 8.04

How do i identify my graphics card?
How would i get a driver from add/remove or the website ie nvidia,ati??

---

### Post by badfish591 on 2008-05-24
have you tried checking under restricted drivers and seeing if it's there?

---

### Post by 2j4ez on 2008-05-24
I went to system>admin>hardware drivers nothing was listed did i goto the right place or is there some where else should goto?

Thanks for your time

---

### Post by Apresmode on 2008-05-24
If Restricted Drivers is not showing, you can choose System > Administration > and Hardware Drivers.  (I think that's what it is)  You may see a driver with a red circle next to it. check enable on it and do what it say ignoring any stuff about free use and then reboot your machine.  Your Graphics Card should now be working.  Ubuntu may still give you messages about it not being fre, but you paid for the computer so oh well, right.

---

### Post by 2j4ez on 2008-05-24
been there nothing is showing also been to add/remove and downloaded ubuntu restricted extras still nothing is showing??

It says "no proprietary drivers in use on this system"

---

### Post by badfish591 on 2008-05-24
well then, what graphics card is in your laptop?

---

### Post by 2j4ez on 2008-05-24
dont no how would i find out? just done a google search it says a 16mb ati

a whopping 16mb of grapics

---

### Post by criskat777 on 2008-05-24
just go to synaptic and install EnvyNG after it is installed click on Ati driver install and it will find and install the proper drivers for your hardware for you. click on yes when it ask if you want it to conf you monitor and yes to restart and that is it. let us know if it work

---

### Post by nebben11 on 2008-05-25
I dont think you'll be able to get any desktop efx with 16mb. My server has 32mb nvidia and wont do any thing and the drivers are enabled I just didnt care because its a server.

---

### Post by Marat Galiev on 2008-05-25
I have integrated Intel Video on my pc,and compiz works well.
Install drivers for you ati with envy,or from:
[http://packages.ubuntu.com/hardy/xorg-driver-fglrx](http://packages.ubuntu.com/hardy/xorg-driver-fglrx)
Read about supported cards,and find you in supported cards list.

---

### Post by 2j4ez on 2008-05-25
it cannot find my card so i tried a manual install at my own risk it asked my to reboot, upon reboot my machine asked my for a graphic driver so i selected ATI now my machine screen res wont go above 640x480
I went to the ENV program in applications>system tools>EnvyNG and selected uninstall ati driver but still got 640x480 the icons are so big !

Anyway to get back to 1024x768? screen res wont go above 640x480

---

### Post by nebben11 on 2008-05-25
Heres what you do...
Reinstall envy ati driver
restart computer
now type this in the a terminal:
> sudo gedit /etc/X11/xorg.conf
than enter your password
this is the driver config file for video, mouse, keyboard, etc
My video section looks like this:
> Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Monitor		"Acer AL1916"
	SubSection "Display"
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection
now where it says "Modes" you want to put in the display modes. once done save, close, and press "ctrl+alt+backspace" this forces X11 to restart and kick you back to the login screen login and see if you have 1024x768 in the resolution settings (note: I woulnt go over 1024x768 you LCD and vid card may not like it).
BTW 2j4ez what is the name and model number of you laptop?

---

### Post by 2j4ez on 2008-05-26
IBM thinkpad r40E 2ghz celeron 1gbram 20gb hdd only paid 40quid for it so its not all bad

just tried your idea but still only got 800x600 and 640x480 i think i will reinstall os if i get no luck

---

### Post by nebben11 on 2008-05-26
I wouldnt its a waste of time it will still do the same thing
post your xorg.conf file

---

### Post by 2j4ez on 2008-05-26
Just ran the madriva live cd it finds my graphic card as a radion IGP 330 and the desktop effects work anyway to use the driver from the madriva cd?
just tried a new ati driver still got my screen at 800x600 it says ubuntu is running in low graphics mode


# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
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
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:5:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"IBM"
	Modelname	"IBM 2113"
	Horizsync	31.0-38.0
	Vertrefresh	50.0-80.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"800x600@60"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"dri"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:5:0"
	Driver		"ati"
	Screen	1
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by nebben11 on 2008-05-26
found the problem
> 
Section "Monitor"
Identifier "Configured Monitor"
Vendorname "IBM"
Modelname "IBM 2113"
Horizsync 31.0-38.0
Vertrefresh 50.0-80.0
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
modeline "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
Gamma 1.0
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
Defaultdepth 24
SubSection "Display"
Depth 24
Modes "800x600@60" "800x600@56" "640x480@75" "640x480@72" "640x480@60"
EndSubSection
EndSection

this will fix it
> Section "Monitor"
Identifier "Configured Monitor"
Vendorname "IBM"
Modelname "IBM 2113"
Horizsync 31.0-38.0
Vertrefresh 50.0-80.0
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
modeline "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1024x768@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1024x768@72" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1024x768@75" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
Gamma 1.0
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
Defaultdepth 24
SubSection "Display"
Depth 24
Modes "1024x768@60" "1024x768@72" "1024x768@75" "800x600@60" "800x600@56" "640x480@75" "640x480@72" "640x480@60"
EndSubSection
EndSection
This should work just use "sudo gedit /etc/X11/xorg.conf" to edit and save it
when done press ctrl+alt+backspace to restart gnome

---

### Post by 2j4ez on 2008-05-26
going to try it now here goes

---

### Post by nebben11 on 2008-05-26
opps i made a mistake I was going off a old xorg.conf file here is the fix

> Section "Monitor"
Identifier "Configured Monitor"
Vendorname "IBM"
Modelname "IBM 2113"
Horizsync 31.0-38.0
Vertrefresh 50.0-80.0
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
modeline "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 +hsync +vsync
modeline "1024x768@72" 75.0 1024 1048 1184 1328 768 771 777 806 +hsync +vsync
modeline "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
Gamma 1.0
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
Defaultdepth 24
SubSection "Display"
Depth 24
Modes "1024x768@60" "1024x768@72" "1024x768@75" "800x600@60" "800x600@56" "640x480@75" "640x480@72" "640x480@60"
EndSubSection
EndSection
This should work just use "sudo gedit /etc/X11/xorg.conf" to edit and save it
when done press ctrl+alt+backspace to restart gnome

---

### Post by 2j4ez on 2008-05-26
I copied and pasted the lines of text and still not able to go above 800x600 it also says my monitor is unknown

---

### Post by nebben11 on 2008-05-26
> **2j4ez said:**
> I copied and pasted the lines of text and still not able to go above 800x600 it also says my monitor is unknown

It will say unknown monitor
Did you try restarting the computer??

---

### Post by wootah on 2008-05-26
Future reference--to find your video card type (manufacturer & model):
```
lspci | grep VGA
```

---

### Post by 2j4ez on 2008-05-26
My desktop is running at 1024x768 thanks anyway to verify the driver is installed?

desktop effects still dont work it says cannot enable desktop effects

---

### Post by nebben11 on 2008-05-26
Did you enable the restricted drivers?
System > Administration > Hardware drivers

---

### Post by 2j4ez on 2008-05-27
Went there nothing is showing up it says 

"NO PROPRIETARY DRIVERS ARE IN USE IN THIS SYSTEM"

---

### Post by nebben11 on 2008-05-27
Have you tryed using envy?

---

### Post by 2j4ez on 2008-05-27
tried that but my card is not found if i do a manual install it forces ubuntu into low graphics mode

---

### Post by nebben11 on 2008-05-27
Try this... First find out what graphics card you have like ati fx1131B for example and from what I can remember in "low graphics mode" you'll be able to select your graphics card.

---

### Post by 2j4ez on 2008-05-27
lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

going to try that now

---

