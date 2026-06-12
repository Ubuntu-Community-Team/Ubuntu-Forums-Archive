---
title: "screen size with different screen resolution ?"
date: 2005-04-23
forum: Hardware &amp; Laptops
---

### Post by johncoom on 2005-04-23
I have an AOpen Openbook 1545D (it is similar to an  Acea - eg. Acea own AOpen).
This AOpen Laptop has a 15 inch wide screen and the physical screen size = 1400 x 1050

My problem is that to get it to fill the screen I have to use 1400 x 1050 which is fine BUT things are far to small (I have already used System -> Preferences -> Font to  increase various text sizes)

What I would like to have is a physical Screen Size of 1400 x 1050 and a virtual Screen Resolution of 800 x 600

You might like to note that this Laptop is multi-booting with Mandrake where I have managed to setup the physical Screen Size to 1400 x 1050 complete with the Virtual Screen Resolulotion of 800 x 600 - So it is possible to do it ?

Because Mandrake's xorg.conf is symlinked to the old style XF86Config-4 and the way it is written is quite a bit different to Ubuntu's /etc/X11/xorg.conf I can not work out how to change the Ubuntu's xorg.conf to allow me to use a 800 x 600 Resolution within a physical Screen Size of 1400 x 1050

If any one knows  hows to do it I would be very gratefull for any tips. Following are the relevent sections from BOTH the Ubuntu and Mandrake files. And you should notice how in the MDK it first defines the physical Screen Size which then after lets you define a Virtual Screen Resolution of what ever you want.
This is what I can not work out how to do in the Ubuntu 5.04 /etc/X11/xorg.conf because they are written diffently :-(


(1) Extract from my Ubuntu 5.04 - /etc/X11/xorg.conf

Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 Go]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-67
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 Go]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection



(2) Extract from Mandrake 10.1 /etc/X11/XF86Config-4
NOTE: MDK's xorg.conf is a symlink to the above file

Section "Monitor"
    Identifier "monitor1"
    VendorName "Generic"
    ModelName "Flat Panel 1400x1050"
    HorizSync 31.5-90
    VertRefresh 59-75
    
    # Sony Vaio C1(X,XS,VE,VN)?
    # 1024x480 @ 85.6 Hz, 48 kHz hsync
    ModeLine "1024x480"    65.00 1024 1032 1176 1344   480  488  494  563 -hsync -vsync
    
    # Dell D800 and few Inspiron (16/10) 1280x800
    ModeLine "1280x800"  147.89  1280 1376 1512 1744  800 801 804 848
    
    # Dell D800 and few Inspiron (16/10) 1680x1050
    ModeLine "1680x1050"  214.51  1680 1800 1984 2288  1050 1051 1054 1103
    
    # Dell D800 and few Inspiron (16/10) 1920x1200
    ModeLine "1920x1200" 230 1920 1936 2096 2528 1200 1201 1204 1250 +HSync +VSync
    
    # TV fullscreen mode or DVD fullscreen output.
    # 768x576 @ 79 Hz, 50 kHz hsync
    ModeLine "768x576"     50.00  768  832  846 1000   576  590  595  630
    
    # 768x576 @ 100 Hz, 61.6 kHz hsync
    ModeLine "768x576"     63.07  768  800  960 1024   576  578  590  616
EndSection

Section "Device"
    Identifier "device1"
    BoardName "NVIDIA GeForce2 Integrated (generic)"
    Driver "fbdev"
    Option "DPMS"
EndSection

Section "Screen"
    Identifier "screen1"
    Device "device1"
    Monitor "monitor1"
    DefaultColorDepth 16
    
    Subsection "Display"
        Depth 8
        Virtual 800 600
    EndSubsection
    
    Subsection "Display"
        Depth 15
        Virtual 800 600
    EndSubsection
    
    Subsection "Display"
        Depth 16
        Virtual 800 600
    EndSubsection
    
    Subsection "Display"
        Depth 24
        Virtual 800 600
    EndSubsection
EndSection


PLEASE ONLY REPLIES FROM PEOPLE WHO KNOW HOW TO DO IT - DO NOT OFFER A GUESS as they are more than often not very usefull

---

### Post by nad on 2005-04-24
If you wish to wait for someone with identical hardware in the same configuration with the same computer who has set up their screen in ubuntu the same way you wish to, stop reading here and do so.

If you are willing to accept that what we offer is free advice from our experiences with sometimes similar hardware and configurations, based on often sketchy information such as yours, I won't guess, just offer some pointers and you can do with it what you wish.

That out of the way, the first thing that would be helpful is both complete files, in a code box (<code>....</code>) please.

My first pointer: You are using two different video drivers. The nv driver in ubuntu and the fbdev in mandrake.

Secondly: The HSync and VRefresh rates are different.

What have you changed from ubuntu's auto configuration. What were the results? Please post the auto configured file. 

I reserve the offer of further pointers until I can review the complete files and the answers to your questions.

Dan M

---

### Post by johncoom on 2005-04-24
Ok Dan M - thanks I will accept your offer and I will have a go at this code thing thought I can not see any easy or obvious explination of how to do it (am I stupid or some thing) ? let me try from your example. Ah after a couple of trys. I think I worked out the code box thing now ? I even worked out the Hyperlink as well, simple when you know how :-(

You Know Dan M - I do not mind if you ignore the MDK one completely - I only offered it as an Example that it could be done. The fact that it uses different nVida and the HSync and VRefresh rates are different is not important.
I think it is best if we assume that the Ubuntu installer has got it right. So if you only offer advice on how to do it from the Ubuntu 5.04 xorf.conf I will be more than happy. 

First the FULL original Ubuntu 5.04 xorg.conf . NOTE:- I have NOT changed any thing at all yet from the original Ubuntu's auto configuration


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
# again, run the following commands:
#
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
	Identifier	"NVIDIA Corporation NV11 [GeForce2 Go]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-67
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 Go]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
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

Next the MDK XF86Config (the xorg.conf is a symlink to it) And as you can see I have been using it through many distro versions - EG: I had got my Touchpad working long before all Linux Distros were doing it (autodetecting). Thanks to the site  [Tuxmobile](http://www.tuxmobil.org/touchpad_driver.html)
OK now the MDK one

```
# File generated by XFdrake.
# FILE EDITED BY JOHN TO USE EITHER USB-MOUSE OR ONBOARD TOUCHPAD (09-Jan-2003)

# **********************************************************************
# Refer to the XF86Config man page for details about the format of
# this file.
# **********************************************************************

Section "Files"
    # Multiple FontPath entries are allowed (they are concatenated together)
    # By default, Mandrake 6.0 and later now use a font server independent of
    # the X server to render fonts.
    FontPath "unix/:-1"
EndSection

Section "ServerFlags"
    #DontZap # disable <Crtl><Alt><BS> (server abort)
    #DontZoom # disable <Crtl><Alt><KP_+>/<KP_-> (resolution switching)
    AllowMouseOpenFail # allows the server to start up even if the mouse doesn't work
EndSection

Section "Module"
    Load "dbe" # Double-Buffering Extension
    Load "v4l" # Video for Linux
    Load "extmod"
    Load "type1"
    Load "freetype"
    
    ###################################### Load "glx" # 3D layer
    Load "synaptics" # onboard touchpad
EndSection

Section "InputDevice"
    Identifier "Keyboard1"
    Driver "keyboard"
    Option "XkbModel" "pc105"
    Option "XkbLayout" "us"
    Option "XkbOptions" ""
EndSection

Section "InputDevice"
    Identifier "Mouse1"
    Driver "mouse"
    Option "Protocol" "ExplorerPS/2"
    Option "Device" "/dev/mouse"
    Option "ZAxisMapping" "6 7"
EndSection

Section "InputDevice"
    Identifier "SynapticsMouse1"
    Driver "synaptics"
    Option "Protocol" "auto-dev"
    Option "Device" "/dev/input/mice"
    Option "MaxSpeed" "0.12"
    Option "MinSpeed" "0.06"
    Option "BottomEdge" "4200"
    Option "SHMConfig" "on"
    Option "LeftEdge" "1700"
    Option "FingerLow" "25"
    Option "MaxTapTime" "180"
    Option "MaxTapMove" "220"
    Option "FingerHigh" "30"
    Option "VertScrollDelta" "100"
    Option "TopEdge" "1700"
    Option "RightEdge" "5300"
    Option "AccelFactor" "0.0010"
EndSection

Section "Monitor"
    Identifier "monitor1"
    VendorName "Generic"
    ModelName "Flat Panel 1400x1050"
    HorizSync 31.5-90
    VertRefresh 59-75
    
    # Sony Vaio C1(X,XS,VE,VN)?
    # 1024x480 @ 85.6 Hz, 48 kHz hsync
    ModeLine "1024x480"    65.00 1024 1032 1176 1344   480  488  494  563 -hsync -vsync
    
    # Dell D800 and few Inspiron (16/10) 1280x800
    ModeLine "1280x800"  147.89  1280 1376 1512 1744  800 801 804 848
    
    # Dell D800 and few Inspiron (16/10) 1680x1050
    ModeLine "1680x1050"  214.51  1680 1800 1984 2288  1050 1051 1054 1103
    
    # Dell D800 and few Inspiron (16/10) 1920x1200
    ModeLine "1920x1200" 230 1920 1936 2096 2528 1200 1201 1204 1250 +HSync +VSync
    
    # TV fullscreen mode or DVD fullscreen output.
    # 768x576 @ 79 Hz, 50 kHz hsync
    ModeLine "768x576"     50.00  768  832  846 1000   576  590  595  630
    
    # 768x576 @ 100 Hz, 61.6 kHz hsync
    ModeLine "768x576"     63.07  768  800  960 1024   576  578  590  616
EndSection

Section "Device"
    Identifier "device1"
    BoardName "NVIDIA GeForce2 Integrated (generic)"
    Driver "fbdev"
    Option "DPMS"
EndSection

Section "Screen"
    Identifier "screen1"
    Device "device1"
    Monitor "monitor1"
    DefaultColorDepth 16
    
    Subsection "Display"
        Depth 8
        Virtual 800 600
    EndSubsection
    
    Subsection "Display"
        Depth 15
        Virtual 800 600
    EndSubsection
    
    Subsection "Display"
        Depth 16
        Virtual 800 600
    EndSubsection
    
    Subsection "Display"
        Depth 24
        Virtual 800 600
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier "layout1"
    InputDevice "Keyboard1" "CoreKeyboard"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "SynapticsMouse1" "AlwaysCore"
    Screen "screen1"
EndSection
``` 

OK Dan M - I hope that is how you wanted it ? Any advice you may offer how it can be done with similar hardware will be most appreciated (I just mentioned that thing about please no guessing as in the past when asking a question of this complexity I have had people who have had not got a clue giving rubbish idea's. I am sure you can understand what I mean) I am  sure that your reply will be much more usefull.

Yours John

---

### Post by nad on 2005-04-24
Thanks John. Sorry for the rough start. I will post back later with some suggestions.

---

### Post by johncoom on 2005-04-24
[QUOTE=nad]Thanks John. Sorry for the rough start. I will post back later with some suggestions.[/QUOTE]

no problem - just so you know - Ubuntu 5.04 did get it correct and the onboard video card of the AOpen Openbook 1545D (very similar to Acer <- I spelt Acer wrong before dubo me) is definalty a - "NVIDIA Corporation NV11 [GeForce2 Go]" - well I am not sure about the NV11 bit but it is definatly a  "GeForce2 Go"

I could never get it working very well in MDK and had to often use a Generic type.
As you can see from above Ubuntu 5.04 seems to have got it right (Like Knoppix does)

OK I will check back later tomorrow - BTW FYI - I am downunder in Melbourne Australia

---

### Post by nad on 2005-04-25
In the Section "Screen", add the Virtual option under your default color depth:

 SubSection "Display"
   Depth   24
   Virtual   800 600   
   Modes   "1400x1050"
 EndSubSection

That ought to do it. As long as the nv driver understands.

---

### Post by johncoom on 2005-04-25
[QUOTE=nad]In the Section "Screen", add the Virtual option under your default color depth:

 SubSection "Display"
   Depth   24
   Virtual   800 600   
   Modes   "1400x1050"
 EndSubSection

That ought to do it. As long as the nv driver understands.[/QUOTE]

No it did not work - all I got was window about 1/2 the size of the physical screen
And its exactly the same as what I get from System -> Preferences -> Screen Resolution

I thought it might be a little more complex, which is why I did not try playing with it before

If you got any other idea's they would be appreciated ?
Mean while I might have a look at the xorg site and see if there are any hints

Again thanks for your efforts, all the best, yours John

---

### Post by nad on 2005-04-25
In the Monitor section, add a DisplaySize option with the directly measured width and height of your monitor in milimeters. 

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
        DisplaySize    width height
	HorizSync	30-67
	VertRefresh	50-75
EndSection

If this does not do it I can only further suggest trying the fbdev driver to see if it generates a valid modeline, add that to the monitor section and delete the Modes option next to the recently added Virtual option. Or just try the fbdev driver. I know that the nv driver is limited.

---

