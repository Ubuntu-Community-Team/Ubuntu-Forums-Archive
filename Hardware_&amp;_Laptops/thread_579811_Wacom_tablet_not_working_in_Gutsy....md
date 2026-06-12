---
title: "Wacom tablet not working in Gutsy..."
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by mister_k81 on 2007-10-18
Hello, I just did a fresh install of 7.10 Gutsy Gibbon today and I seem to be having problems with my Wacom tablet. Ubuntu does detect it, but it is not working right at all. For example I can't move the mouse cursor around while hovering the pen over the tablet base.  

It did work fine in Feisty, but not here. I'm not sure if there's something that I'm suppose to do to enable it properly, or what? The X.Org X server wacom input driver is installed, so are the wacom tools utilities ...  My tablet is a Wacom Graphire 4  6x8 (if that makes any difference at all?). Any help would be appreciated. :confused:

---

### Post by graigsmith on 2007-10-18
mines not working either. i thought it was supposed to be auto-detected in this version?

---

### Post by mister_k81 on 2007-10-18
Sorry about bumping this thread, but does anyone here have any suggestions on how I could fix this problem?

---

### Post by Rudism on 2007-10-19
Check the end of your /etc/X11/xorg.conf file for something in the "ServerLayout" section that looks like this:

```
# Uncomment if you have a wacom tablet
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
```

The three lines were commented by default in my Gutsy install. Uncommenting them fixed my problems.

---

### Post by mister_k81 on 2007-10-19
Thanks Rudism! That fixed it.  :D

---

### Post by samba on 2007-10-19
Same problem here with a Toshiba Portege tablet pc. Uncommenting the three lines in xorg.conf also worked. However perhaps that should be done by default since most users will not know that they have to do that. In fact I don't know why it's not enabled by default with 7.10, since it was with previous Ubuntu versions.

Thanks! :-)
vincent

---

### Post by disciplefk on 2007-10-19
Anyone know how to program buttons on the wacom tablet?  I want to assign shortcut keys to buttons, but they dont seem to function at all

---

### Post by mairabc on 2007-10-20
Hello,

you can try using expresskeys:

[http://freshmeat.net/projects/wacomexpresskeys/](http://freshmeat.net/projects/wacomexpresskeys/)

The package has installation instructions. Then you can check these urls for instructions as how to configure the pad:

[http://gentoo-wiki.com/HOWTO_Wacom_Tablet#Graphire4_buttons](http://gentoo-wiki.com/HOWTO_Wacom_Tablet#Graphire4_buttons)
[http://foto-cs.de/blog/item/196](http://foto-cs.de/blog/item/196)

Problem is, I am not being able to make this work in Gutsy. In Feisty it worked perfectly. I saw that there is already a bug about it here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/59570/](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/59570/)

I already added one comment. Maybe you would want to keep an eye there as well.

Good luck =)
Maira

---

### Post by memm74 on 2007-10-23
> **Rudism said:**
> Check the end of your /etc/X11/xorg.conf file for something in the "ServerLayout" section that looks like this:

```
# Uncomment if you have a wacom tablet
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
```

The three lines were commented by default in my Gutsy install. Uncommenting them fixed my problems.

If I do this on my Gutsy the graphical interface will not start anymore. The first time I tried it and it stopped working  I had to do a "sudo dpkg-reconfigure xserver-xorg" to get it working again. Is there another way of getting it to work properly? (Moving the cursor works, and double-clicks do, but nothing else seems to work, e.g. painting in GIMP)

---

### Post by elvismagrelo on 2007-10-24
DONE! 

&#8226; It's better to install the wacom tools via terminal:

sudo apt-get install xserver-xorg-input-wacom wacom-tools

&#8226; Make a backup of xorg.conf:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

&#8226; After, to open the xorg.conf file, use this command:

gksudo gedit /etc/X11/xorg.conf

&#8226; In the last lines search for this section:

# Uncomment if you have a wacom tablet
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"

- Uncomment, means you have to remove the "comment" sign (#) from this three lines, like the example below:

# Uncomment if you have a wacom tablet
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"




Save it, reboot, and i'ts done!
Other configurations you find here:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

Cheers!
Bira

---

### Post by memm74 on 2007-10-26
I followed the instructions, those lines are uncommented... I got X11 working now again, and the pen can move the mousepointer, i can use the two buttons on the pen, but if I touch the board with the pen (i.e. should be a left mouse click) nothing happens in Ubuntu. The board does however register it because the LED changes from blue to green every time I press the pen down. (It's a Wacom graphire 4).

---

### Post by Dan_Dranath999 on 2007-10-30
The Bamboo doesn't work at all... even with those lines uncommented...

---

### Post by pixelstuff on 2007-10-30
hi
I also lost the pressure sensitivity on my graphire 3 after the gutsy update. everthing still installed and the famous lines uncommented...the tablet works like a mouse but is not recognized as a tablet by the programms. Only system -> preferences -> hardware information shows it. When I type
[HTML]sudo lshw[/HTML] it does not list any individual usb devices at all, only usb-contoller 0 - 4 and vendor "intel corp" Now I have to boot to windows for work - what can I do? :(

---

### Post by bigdee973 on 2007-11-06
ok i have an intuos 3 tablet, model ptz 431w,  and i followed the instructions but no show,  i hover my pen over the tablet and nothing happens, if i press the tablet i can move the cursor very little. and when i go to gimp it says theres no extended input device in perference,   heres my xorg.conf setting please tell me if i did something wrong 
i modified it this way   [http://ubuntuforums.org/showthread.php?t=25151](http://ubuntuforums.org/showthread.php?t=25151)


# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"   #USB ONLY
  Option        "Type"          "stylus"
  Option        "USB"           "on"                  #USB ONLY
  Option        "ForceDevice"   "ISDV4"               #Tablet PC ONLY
	Option "PressCurve" "50,0,100,50"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"   #USB ONLY
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  #USB ONLY
  Option        "ForceDevice"   "ISDV4"               #Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"   #USB ONLY
  Option        "Type"          "cursor"
  Option        "Mode"          "relative"
  Option        "USB"           "on"                  #USB ONLY
  Option        "ForceDevice"   "ISDV4"               #Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"   #USB ONLY
  Option        "Type"          "pad"
  Option        "USB"           "on"                  #USB ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Modelname	"Custom 1"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1400	1050
		Modes		"1400x1050@60"	"1280x1024@60"	"1280x960@60"	"1152x864@75"	"1024x768@43"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"1024x768@85"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"  
        InputDevice    "pad"
	InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
	
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
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

### Post by yesudeep on 2007-11-06
The bamboo doesn't work for me either with those lines uncommented.

Wacom-tools version 0.7.7 (which comes with Gutsy) does not support Bamboo.
Versions higher than 0.7.8-3 do, but...

Kernel 2.6.22 is not supported by Linuxwacom version 0.7.8-3.
Linuxwacom version 0.7.9-dev supports kernel 2.6.22.  However, even
after following the instructions at [http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/)
I haven't been able to get my Bamboo to work!

If someone gets their Bamboo working, please please please let us know.
I'd like to get rid of Windows ASAP.

Regards,
Yesudeep.

---

### Post by bigdee973 on 2007-11-06
OK, never mind, i fixed the problem, i just deleted all the lines that had the comments #serial only and #"tablet Pc" from xorg.conf and the thing works flawlessly, now the only problem now is that i want the little touch pad thats on the side of the tablet that lets me zoom in and zoom out in adobe photoshop in windows to work just like that in gimp.  i run my fingers up and down on the pad and it runs thru icons rather than zoom in and zoom out.  also theres no button configurations set up for the tablet, i wanna add the basic functions like alt, shift, ctrl and what have u onto the buttons, could someone give me more details?,  I'm using gutsy of course with all the latest updates since nov 6 07, please help:(

p.s. i also want to have the same eraser function in gimp just like i would have it in adobe photoshop in windows where when i turn the pen around onto the "eraser"s side the icon switches automatically to the eraser function and im able to erase and when i switch over to the pen tip it automatically goes back into the brush, pen or whatever have u.  any advice would be the pleasant since i no longer would see any use of using crap-indows.  thank u

---

