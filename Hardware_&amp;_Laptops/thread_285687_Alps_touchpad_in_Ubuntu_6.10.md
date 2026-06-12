---
title: "Alps touchpad in Ubuntu 6.10"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by Jaxilian on 2006-10-27
Please tell me that they added an option to turn off the tapping for ALPS touchpad in this new Ubuntu version :-k 

That never worked in Ubuntu 6.06. Any checked it?

---

### Post by MagnusL on 2006-10-30
Hi!
On my Toshiba Portege M200, the Alps touchpad works but I cannot disable tapping. I could in dapper, by setting MaxTapTime to "0" in xorg.conf. 

Magnus L

---

### Post by Jaxilian on 2006-10-31
> **MagnusL said:**
> Hi!
On my Toshiba Portege M200, the Alps touchpad works but I cannot disable tapping. I could in dapper, by setting MaxTapTime to "0" in xorg.conf. 

Magnus L

gaaah....that sux! I don't get what is so hard to fix. Tapping is the most annoying thing on a laptop. It's one of many things that makes me wanna run Windows again.
I hope Ubuntu team will fix this A.S.A.P. ](*,)

---

### Post by didobuntu on 2006-10-31
> **flodis said:**
> Please tell me that they added an option to turn off the tapping for ALPS touchpad in this new Ubuntu version :-k 

That never worked in Ubuntu 6.06. Any checked it?

Hello,

I have an asus and I hope this could serve for a Toshiba. I modified the xorg.conf file as follows to turn on/off the touchpad:

1. Add the line - InputDevice  "touchpad" "AlwaysCore" - in the ServerLayout section to get something like this:

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "touchpad" "AlwaysCore"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection
	
	
2. Add of modify the InputDevice Section concerning the touchpad

Section "InputDevice"
	Identifier  "touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
	Option	    "ShmConfig" "true"
EndSection


reboot and see if you enable/disable the touchpad now

---

### Post by Jaxilian on 2006-11-21
> **didobuntu said:**
> Hello,

I have an asus and I hope this could serve for a Toshiba. I modified the xorg.conf file as follows to turn on/off the touchpad:

1. Add the line - InputDevice  "touchpad" "AlwaysCore" - in the ServerLayout section to get something like this:

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "touchpad" "AlwaysCore"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection
	
	
2. Add of modify the InputDevice Section concerning the touchpad

Section "InputDevice"
	Identifier  "touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
	Option	    "ShmConfig" "true"
EndSection


reboot and see if you enable/disable the touchpad now

no, doesnt work. So far I have seen none that has been able to disable tapping on Alps. I can't write any mails or letters when tapping is enabled. it just makes it impossible when it so sensitive.

---

### Post by Jaxilian on 2006-11-21
This sux so royal when I can't disable tapping. Anyone that has tried writing a letter on a laptop with supersensitive touchpad knows what I am talking about. As of now I can almost breathe on my touchpad to make the pointer move.

Of course in windows I can disable/adjust this without problems. How can this be so hard in ubuntu? This problem has been in the 2 latest versions and I bet this problem as it looks now, will be in the version 10 still.
I am so frustrating about this you can't believe ](*,)  :evil:  :(

---

### Post by Sencer on 2006-11-21
Here people have successfully disabled tapping for their alps touchpad:
[http://ubuntuforums.org/showthread.php?t=78904](http://ubuntuforums.org/showthread.php?t=78904)

---

### Post by Jaxilian on 2006-11-22
> **Sencer said:**
> Here people have successfully disabled tapping for their alps touchpad:
[http://ubuntuforums.org/showthread.php?t=78904](http://ubuntuforums.org/showthread.php?t=78904)


tried that, but my X crashed then. Any out there that can help me? :confused:

---

### Post by Jaxilian on 2006-11-22
when I run this command
```

 cat /proc/bus/input/devices

```

I get this:
```

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input6
H: Handlers=mouse1 event2 ts1 
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

```

and my xorg.conf looks like this:
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
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
	Option		"XkbLayout"	"se"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
        Option  "Composite" "Disable"
EndSection


```

Please help!
](*,)

---

### Post by Jaxilian on 2006-11-23
ok I changed my Xorg.conf to this:

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
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
	Option		"XkbLayout"	"se"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier "ALPS"
	Driver "synaptics"
	Option "CorePointer"
	Option "Device" "/dev/input/event2"
	# Option "Device" "/dev/psaux"
	# Option "Device" "/dev/input/mice"
	# Option "Protocol" "auto-dev"
	Option "Protocol" "event"
	Option "LeftEdge" "120"
	Option "RightEdge" "830"
	Option "TopEdge" "120"
	Option "BottomEdge" "650"
	Option "FingerLow" "14"
	Option "FingerHigh" "15"
	Option "MaxTapTime" "180"
	Option "MaxTapMove" "110"
	Option "ClickTime" "0"
	Option "EmulateMidButtonTime" "75"
	Option "VertScrollDelta" "10"
	Option "HorizScrollDelta" "10"
	Option "MinSpeed" "0.45"
	Option "MaxSpeed" "0.75"
	Option "AccelFactor" "0.020"
	Option "EdgeMotionMinSpeed" "200"
	Option "EdgeMotionMaxSpeed" "200"
	Option "UpDownScrolling" "1"
	Option "CircularScrolling" "0"
	Option "CircScrollDelta" "0.1"
	Option "CircScrollTrigger" "2"
	Option "SHMConfig" "true"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	 "ALPS"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
        Option  "Composite" "Disable"
EndSection

```

and the output from Xorg.0.log is: 
```

(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "se"
(**) Generic Keyboard: XkbLayout: "se"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) Synaptics touchpad driver version 0.14.6 (1406)
(**) Option "Device" "/dev/input/event2"
(**) Option "SHMConfig" "true"
(**) Option "LeftEdge" "120"
(**) Option "RightEdge" "830"
(**) Option "TopEdge" "120"
(**) Option "BottomEdge" "650"
(**) Option "FingerLow" "14"
(**) Option "FingerHigh" "15"
(**) Option "MaxTapTime" "0"
(**) Option "MaxTapMove" "0"
(**) Option "ClickTime" "0"
(**) Option "EmulateMidButtonTime" "75"
(**) Option "VertScrollDelta" "10"
(**) Option "HorizScrollDelta" "10"
(**) Option "EdgeMotionMinSpeed" "200"
(**) Option "EdgeMotionMaxSpeed" "200"
(**) Option "UpDownScrolling" "1"
(**) Option "CircularScrolling" "0"
(**) Option "CircScrollTrigger" "2"
(EE) ALPS no synaptics touchpad detected and no repeater device
(EE) ALPS Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "ALPS"
(II) UnloadModule: "synaptics"
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+se+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
(**) RADEON(0): RADEONSaveScreen(2)

```

What am I doin wrong?

---

### Post by Jaxilian on 2006-11-23
I am just about to drive something real sharp through my ALPS shitpad, anyone wanna save it? ](*,)

---

### Post by Elaztic on 2006-11-24
I have a Dell D820 with Alps touchpad and 'glidepoint' and also have trouble configuring it.
Worst problem is how to turn off the 'glidepoint' and set the speed og the touchpad and 'vertical scrolling'.

In Windows there is a quite elaborate configuration tool...why in the world won't alps make one similar to linux??

I have a xorg.conf similar to the ones posted above but no luck... :(

Help me please....

---

### Post by tsukurite on 2006-12-11
I'm in FC5, but it's on a d820 (Waiting on a second drive to start playing with Ubuntu)  Do you have the synaptics driver installed?  
I recall I had to google for it, but there's one out there.  I got mine from here:
[http://web.telia.com/~u89404340/touchpad/index.html]("http://web.telia.com/~u89404340/touchpad/index.html")

There is a full explanation of the flags that are available, including dealing with tapping.

Here's my xorg.conf.

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Tue Aug  1 21:11:12 PDT 2006

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Synaptics Mouse"  "AlwaysCore"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
    FontPath        "unix/:7100"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
    Load           "synaptics"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/mice"
    Option         "Emulate3Buttons" "yes"
    Option         "ZAxisMapping" "4 5"
EndSection

#    Option "Protocol"  "Auto"
#    Option "Device" "/dev/input/event3" # (cat /proc/bus/input/devices)
#    Option "Name" "Logitech MX1000"
#    Option "Buttons"    "7"
#    Option "ZAxisMapping" "4 5"
#    Option "Resolution" "800"
#EndSection

Section "InputDevice"
  Driver        "synaptics"
  Identifier    "Synaptics Mouse"
  Option        "Device"        "/dev/psaux"
  Option        "Protocol"      "auto-dev"
  Option        "LeftEdge"      "1700"
  Option        "RightEdge"     "5300"
  Option        "TopEdge"       "1700"
  Option        "BottomEdge"    "4200"
  Option        "FingerLow"     "25"
  Option        "FingerHigh"    "30"
  Option        "MaxTapTime"    "180"
  Option        "MaxTapMove"    "220"
  Option        "VertScrollDelta" "100"
  Option        "MinSpeed"      "0.09"
  Option        "MaxSpeed"      "0.18"
  Option        "AccelFactor"   "0.0015"
  Option        "SHMConfig"     "on"
EndSection

Section "InputDevice"
    # generated from data in "/etc/sysconfig/keyboard"
    Identifier     "Keyboard0"
    Driver         "keyboard"
    Option         "XkbLayout" "us"
    Option         "XkbModel" "pc105"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "AllowGLXWithComposite" "On"
    Option         "RenderAccel" "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200" "1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
Section "Extensions"
        Option "Composite" "true"
EndSection

```

Some of that works and some of it doesn't, but the synaptics bits all work for me.  Having synclient functional should get all the flags working.  Note: this has absolutely no effect on the glidepoint stick, but that's never been an issue for me.

Also, I have a simple bash script to turn the touchpad on and off for those times I'm using an external mouse.

```

#!/bin/bash

state=`synclient -l|grep Touchpad | awk -F"= " '{ print $2 }'`

if [[ "${state}" == "1" ]]; then
    synclient TouchpadOff=0
else
    synclient TouchpadOff=1
fi

```

Hope that helps.

Regards.

---

### Post by Jaxilian on 2006-12-18
Problem solved. 
I switched to SuSe Linux Enterprise Desktop 10.1.

everything works now.

tapping off =works
XGL/Compiz =works

SuSe works better for this computer I think. :KS

---

### Post by Jaxilian on 2007-04-24
Is it possible to get a Ubuntu developer opinion on this?

---

