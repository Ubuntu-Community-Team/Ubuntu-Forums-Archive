---
title: "Desktop does not match screen resolution [Gutsy only?]"
date: 2007-10-04
forum: Hardware &amp; Laptops
---

### Post by Gorgo13 on 2007-10-04
Hi there,

I could not find any thread about this specific problem, sorry if it's been discussed (and solved!) already.

I installed Ubuntu Gutsy Gibbon beta on my Panasonic CF-Y7 laptop. I started with 1280x1024 resolution for install, then I tried to modify the display type and resolution to 1400x1050. Then Ubuntu recognizes the 1400x1050 display and it works, but the desktop resolution is stuck at 1024x768. The login screen is at 1024x768, but fits inside the actual 1400x1050 resolution (like if it was "windowed").

Here is a screenshot of my desktop:
[[IMG]http://img179.imageshack.us/img179/854/desktopfullgh6.th.png[/IMG]](http://img179.imageshack.us/my.php?image=desktopfullgh6.png)

And here is a windowshot of the display panel options: the resolution for the default monitor is stuck at 1024x768 and I cannot select any other higher resolution (even when I select the "LCD 1400x1050" monitor type).

[[IMG]http://img179.imageshack.us/img179/4263/displayoptionsoj9.th.png[/IMG]](http://img179.imageshack.us/my.php?image=displayoptionsoj9.png)

Also the screen rate is 30Hz which obviously is not correct. Also, I do not know if it is wrong or not, but you can see that there are 2 "Screen 1" (in french "Ecran 1") in the list...

Of course I can resize the windows to fit the 1400x1050 display, but as you can see on the first image, the top bar is limited to 1024x768. When I first logged with this configuration, the bottom bar was also reproducing this 1024x768 display (the bar was floating in the middle of the screen and its width was 1024 pixels). But I could resize and move it to the real bottom of the screen, and have its width 1400 pixels (as shown on the first image). 

Thanks in advance for your help. :)

PS: here is my xorg.conf

```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"jp106"
	Option		"XkbLayout"	"jp,jp"
	Option		"XkbVariant"	"latin,"
	Option		"XkbOptions"	"grp:alt_shift_toggle,grp_led:scroll"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Boardname	"intel"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1400x1050"
	Horizsync	31.5-90
	Vertrefresh	59-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1920	1440
		Modes		"1400x1050@60"	"1400x1050@75"	"1280x960@75"	"1600x1200@65"	"1280x1024@60"	"1600x1200@60"	"1280x960@60"	"1600x1200@70"	"1280x1024@75"	"1792x1344@60"	"1152x864@75"	"1856x1392@60"	"1024x768@60"	"1920x1440@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" #    
	Identifier	"device1"
	Boardname	"intel"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	1
EndSection
Section "screen" #    
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #    
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "device" #    
	Identifier	"device2"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:0:2:1"
	Driver		"vesa"
	Screen	0
EndSection
Section "screen" #    
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #    
	Identifier	"monitor2"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by Gorgo13 on 2007-10-04
I forgot to mention that when setting option in the Screen/Resolution panel, it makes it crash (the setting application(?)... i.e. I got a message from the system notification system which states that the app crashed).

---

### Post by stoumpos on 2007-10-04
Have the same problem with gutsy on a Toshiba U300 laptop. Found the
following solution at [http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_Tribe_on_a_ThinkPad_R61]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_Tribe_on_a_ThinkPad_R61")

Modify /etc/X11/xorg.conf so that a new monitor is added for
the tv-out, marked as disabled. Specify on the device section
the name of the dummy tv-out.

add:

Section "Monitor"
    Identifier "TVOutput"
    Option "Disable" "true"
EndSection

find Section "Device" and add:

Option "monitor-TV" "TVOutput"

---

### Post by Gorgo13 on 2007-10-04
Hi stoumpos,

Thanks a lot for the tip! Will try that ASAP and report here if it worked for me or not.

-Gorgo13

---

### Post by Gorgo13 on 2007-10-05
Stoumpos you're the man :)

It worked fine, thanks a lot!

-Gorgo13

---

### Post by yjhuoh on 2007-10-16
thanks for the fix, worked for me too. but any chance of a REAL fix in ubuntu? this seems more like a temporary work-a-round than a fix.

---

### Post by mattclary on 2007-11-04
Praise the lord!!!! That did it!!!!!

I had found a similar but more complex fix that didn't work. The simplicity of this is unbelievable!

FYI, running a Gateway ML6720 at 1280x800 (now!)

:guitar:

---

### Post by skinind95 on 2007-11-15
stoumpos -- Had to register to thank you, this fixed the problem on my Toshiba P205 where my desktop was 1440x900 (correct) and my display was set to only 1280x800 causing a 'zoomed' effect.  I have an S-Video out port and it never crossed my mind that that could be causing the problem. So, Thank You!

,Travis

---

### Post by wrongo on 2007-11-16
> **stoumpos said:**
> Have the same problem with gutsy on a Toshiba U300 laptop. Found the
following solution at [http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_Tribe_on_a_ThinkPad_R61]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_Tribe_on_a_ThinkPad_R61")

Modify /etc/X11/xorg.conf so that a new monitor is added for
the tv-out, marked as disabled. Specify on the device section
the name of the dummy tv-out.

add:

Section "Monitor"
    Identifier "TVOutput"
    Option "Disable" "true"
EndSection

find Section "Device" and add:

Option "monitor-TV" "TVOutput"

Sorry, this is totally basic, but the computer is telling me that I don't have permission to do anything in the /etc/X11/ directory, apparently: I can't even back up the xorg.conf file! I know the sudo chmod +rwx /etc/X11/xorg.conf command, but it doesn't give me permission to save xorg.conf as xorgBACKUP.conf :(

If anyone is reading this, and can help, I'd appreciate it if you took a sec and just helped me with this totally basic problem - then I can get on with fixing my screen resolution.

I'm going to try "sudo dpkg-reconfigure xserver-xorg" in the meantime, and tinker with the default screen resolution.

Denied

---

### Post by wrongo on 2007-11-16
totally worked.

sudo reboot

done and done.

yeah baby

in case you missed it:

sudo dpkg-reconfigure xserver-xorg

then hit ENTER a bunch or TAB then ENTER if the screen doesn't change

then, at "User kernel framebuffer device interface?" choose <YES>

(Actually, that might not matter, but I chose <YES> b/c the dialog text recommended it and mine was coming up with <NO> as the default option - then again, this might be crucial - heck I dunno)

ENTER or TAB then ENTER if the screen doesn't change, just like before, till you get to the screen reading:

&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
  &#9474; Please keep only the resolutions you would like the X server to use.     &#9474;  
  &#9474; Removing all of them is the same as removing none, since in both cases   &#9474;  
  &#9474; the X server will attempt to use the highest possible resolution.        &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474; Video modes to be used by the X server:                                  &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474;    [ ] 1920x1440                                                     &#8593;   &#9474;  
  &#9474;    [ ] 1920x1200                                                     &#9646;   &#9474;  
  &#9474;    [ ] 1856x1392                                                     &#9618;   &#9474;  
  &#9474;    [ ] 1792x1344                                                     &#9618;   &#9474;  
  &#9474;    [ ] 1680x1050                                                     &#9618;   &#9474;  
  &#9474;    [ ] 1600x1200                                                     &#9618;   &#9474;  
  &#9474;    [ ] 1440x900                                                      &#9618;   &#9474;  
  &#9474;    [ ] 1400x1050                                                     &#8595;   &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474;                                  <Ok>                                    &#9474;  
  &#9474;                                               

Check them all - if you dare - and "sudo reboot" the mo-fo

CAUTION: SUDO DPKG-RECONFIGURE XSERVER-XORG CAN TOTALLY BREAK YOUR DISPLAY, IT'S HAPPENED TO ME, IT CAN HAPPEN TO YOU - THE OPERATING SYSTEM WILL COME UP AS TEXT ONLY IN THIS CASE. IF YOU'RE AFRAID THIS MIGHT HAPPEN, WRITE DOWN THE "SUDO DPKG-RECONFIGURE XSERVER-XORG" COMMAND ON A PIECE OF PAPER, SO YOU HAVE IT HANDY IN CASE IT DOES, AND JUST TYPE IT IN. YOU SHOULD BE ABLE TO RESTORE YOUR 'GRAPHICAL USER INTERFACE' OR GUI WITH THIS ONE POWERFUL COMMAND.

---

