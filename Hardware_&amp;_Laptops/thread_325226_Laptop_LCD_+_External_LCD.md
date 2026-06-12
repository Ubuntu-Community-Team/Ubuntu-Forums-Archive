---
title: "Laptop LCD + External LCD"
date: 2006-12-25
forum: Hardware &amp; Laptops
---

### Post by MasterEvilAce on 2006-12-25
I have a Dell Inspiron 8000 with a 1600x1200 LCD.

I also have an external Dell 2007WFP LCD.

I edited my xorg.conf to try and clone my screen so I see the same thing on my internal LCD and external LCD at the same time. Currently, I can only seem to get one or the other.. with my external plugged in, it takes over. If i unplug it, my internal takes over.

I'm wondering how my xorg.conf should look.. any working examples?

---

### Post by dbbolton on 2006-12-25
could you post a copy of yours here ?

---

### Post by MasterEvilAce on 2006-12-25
here it is

---

### Post by MasterEvilAce on 2006-12-25
Bump :(

I even added a separate device/monitor/screen section to my xorg.. Which kinda is getting somewhere.. but not entirely. My external LCD will display what i normally see.. however my laptop then displays a default KDE desktop.. almost like it's logged in under a new user account.....

---

### Post by diverdale on 2006-12-26
Here's a copy of my xorg.conf file...it's a bit convoluted but it works. If I'm docked, it uses both internal and external display (dual haeaded config) If I'm undocked, it just uses the laptop's LCD. It's a Thinkpad T40. Hope it helps.

Dale

---

### Post by MasterEvilAce on 2006-12-26
```

Section "Device"
	Identifier	"Internal Device"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	option "NoLogo" "1"
	option "RenderAccel" "1"
	option "TwinView" "true"
	option "TwinViewOrientation" "Clone"
	option "MetaModes" "DFP-0: 1600x1200, CRT-0: 1680x1050"
EndSection

Section "Monitor"
	Identifier	"Internal Monitor"
	Option		"DPMS"
	HorizSync	30-75
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Internal Screen"
	Device		"Internal Device"
	Monitor		"Internal Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200"
	EndSubSection
	option "DPMS"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen "Internal Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	#option "BlankTime" "10"
	option "StandbyTime" "10"
	option "OffTime" "10"
	option "HWCursor" "true"
EndSection

```



Playing around a lot more with it.. I managed to figure out a lot of stuff.. I think diverdale's is kinda ATI specific.. MergeFB stuff or what not. Not entirely sure.

Anyways, here's my current XORG.CONF.. the relevant parts, anyways.

my laptop is 1600x1200, and my external lcd is 1680x1050. Using the above settings just like they are, I get the same image on both, except my laptop shows the 1680x1050 resolution as well.. which doesn't work too well... I've tried setting both to 1600x1200, but my external monitor complains for some reason, and doesn't turn on. My External should be able to read 1600x1200, and scale it to fit.. but it's not for some reason.

this line is what i have to perfect, i think..
**option "MetaModes" "DFP-0: 1600x1200, CRT-0: 1680x1050"**

Anyone have any ideas?

---

### Post by diverdale on 2006-12-26
I ran into the same issue you're having before I found out about the "dual head" mode. Basically, X doesn't know how to handle displays with different resolutions. If you want to be able to drag stuff between the 2 displays they must be running at the same resolution. If you can get by without that (which takes some gettin used to) you can have different resolutions. It's a long and complicated explination but that's it in a nutshell. Take a look at my section that describes "TwoHeadLayout"...good luck  <edit added snippet below>

Section "ServerLayout"
	Identifier	"TwoHeadLayout"
	Screen		"Screen0"
	Screen		"Screen1" RightOf "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerFlags"
  	Option		"DefaultServerLayout"	"TwoHeadLayout"
........
....
....

Dale

---

### Post by MasterEvilAce on 2006-12-26
Well, that shouldn't apply to me because I'm doing a clone mode configuration. I'll see only one desktop, and it'll be the same on my laptop LCD and on my external.

I guess my ideal solution is to get 1600x1200 to display on both monitors, and have my external just auto-fit to widescreen.. but it's just not accepting my 1600x1200 signal.

to clarify, I got both monitors to display the same desktop.. my external displayed 1680x1050 fine, but my laptop also tried displaying 1680x1050, and it resulted in a scrolling scenario where the screen didn't fit entirely on my the monitor...
and trying to output 1600x1200 to BOTH.. my external just doesn't turn on

---

### Post by diverdale on 2006-12-26
ok...just curious, If you can get your external to display the1680x1050 you want...and it's cloned on your laptop, what difference does it make if your laptop display scrolls? You could just close the lid since you're just seeing duplicates anyhow. Smack me if that's stupid :)

---

### Post by MasterEvilAce on 2006-12-26
because sometimes i'll use the external and other times i wont.. and it would annoy the hell out of me when i wouldn't use the external.. seeing part of the screen cut

---

### Post by diverdale on 2006-12-26
# determine whether an external display is attached
#cp /etc/X11/xorg.conf /etc/X11/xorg.conf.pre-local
if /usr/sbin/ddcprobe | grep -q “analog signal”; then
echo “External Display attached.”
# set external display as exclusive primary
# cat /etc/X11/xorg.conf.pre-local | sed ’s#”Single”#”Single,Reverse”#g’ > /etc/X11/xorg.conf
cp /etc/X11/xorg.dual.conf /etc/X11/xorg.conf
else
echo “Using build-in LCD.”
# set build-in LCD as exclusive primary display
# cat /etc/X11/xorg.conf.pre-local | sed ’s#”Single,Reverse”#”Single”#g’ > /etc/X11/xorg.conf
cp /etc/X11/xorg.conf.orig /etc/X11/xorg.conf
fi


copy the above and name it switcher.sh or whatever...chmod to +x and stick it in /etc/init.d  you'll need to have 2 xorg.conf files that you can copy over one another...it's a hack but it's how I go from single to dual....it that doesn't help, I'm out of ideas :P

---

### Post by joma on 2007-03-15
I use some of the information posted here whith some I found elsewhere to make my internal laptop display work with a projector. Here is the modification I made to my xorg.conf

In the section "Device" I added the following :
>        option "TwinView" "true"
       option "TwinViewOrientation" "Clone"
       Option  "MergedFB" "true"
       Option  "MergedDPI" "100 100"

The projector can handle the resolution of my display so I had nothing more to do.

Regards

---

### Post by pettijok on 2007-12-13
So i am rather new to ubuntu and linux in general and im really having some hard times getting my display on my samsung TFT-LCD LN-T4053H. I am working on a sony fs-660/w laptop (GeForce 6200 Go) with a VGA out. I know this is possible because i had it running in XP and loved it. I have been trying to follow the instructions in many different threads but with no success. 

Something that might be note worthy is my TV i think only supports the resolution of 1360x768 @60hz

Any help would be most welcomed. Thanks!

P.S i know my xorg.conf is a bit messy and i apologies. 






 ```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:30:30 PDT 2007

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:29:35 PDT 2007
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "Monitor"
    Identifier     "Failsafe Monitor"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1280x800"
    HorizSync       31.5 - 50.0
    VertRefresh     56.0 - 65.0
    Gamma           1
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
EndSection

Section "Monitor"

 # 
    Identifier     "monitor1"
    Gamma           1
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 49.0
    VertRefresh     0.0 - 61.0
EndSection

Section "Device"
    Identifier     "Failsafe Device"
    Driver         "nvidia"
    BoardName      "vesa"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device" # 
    Identifier     "device1"
    Driver         "nv"
    BoardName      "vesa"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Failsafe Device"
    Monitor        "Failsafe Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1280 800
        Depth       24
        Modes      "800x600@60" "1280x768@60" "800x600@56" "1280x720@60" "1280x800@60"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x800 +0+0; 800x600@60 +0+0; 800x600@56 +0+0; 1280x720@60 +0+0"
EndSection

```

---

### Post by Shibby73 on 2008-01-16
I have an Acer Travel Mate 800LCi
ATI Mobility Radeon 9000 3D Graphic/64MB RAM (built in).

I typically view my laptop screen at the highest resolution (15" SXGA TFT LCD 1400x1050).
Over Christmas I purchased an external Westinghouse 22" 1600x1080 external LCD monitor.

I'd like to operate the external as either my primary display at its highest resolution or as a dual display that shares the desktop.

Please tell me where to go for instruction on this.
1) How to back up any files I might alter and how to get back to my present state should there be any problems.
2) Any display control interfaces (or shortcuts in Ubuntu) to swtich how/if the external is being used.

When I simply boot with the display attached I get an error on my display that just says "out of range" and can't see anything on my laptop screen but do hear the start-up login "ping" (I'm using UbuntuStudio, which I'd upgrade but I'm afraid of losing my internet connectivity and other programs by changing the Kernal).

I appreciate any help and directions.

~Shibby73~

---

