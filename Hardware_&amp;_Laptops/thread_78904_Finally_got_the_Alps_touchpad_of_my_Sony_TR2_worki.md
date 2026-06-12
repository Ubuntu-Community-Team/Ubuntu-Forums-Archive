---
title: "Finally got the Alps touchpad of my Sony TR2 working in Breezy"
date: 2005-10-19
forum: Hardware &amp; Laptops
---

### Post by scubajeff on 2005-10-19
I have been searching for hints in this forum for quite so while, finally I got the Alps touchpad working. So thank you for all the others who contributed to this issues.

First of all, if you have ever touched the file "/etc/modprobe.d/psmouse.modprobe", please remove it. Since it prevent the system from probing the Alps touchpad. On my Sony TR2, before removing this file, the system only found a PS/2 Generic Mouse, after removing it, the system found a PS/2 Mouse and a Alps Glidepoint.

Next, use the following command to find the correct handler of the Alps touchpad:

[FONT="Fixedsys"]  cat /proc/bus/input/devices[/FONT]

on my system, it shows up something like the following
[FONT="Fixedsys"]
  I: Bus=0011 Vendor=0002 Product=0008 Version=7321
  N: Name="AlpsPS/2 ALPS GlidePoint"
  P: Phys=isa0060/serio1/input0
  H: Handlers=mouse3 event5 ts2
  B: EV=f
  B: KEY=420 0 70000 0 0 0 0 0 0 0 0
  B: REL=3
  B: ABS=1000003
[/FONT]

Then, modify the /etc/X11/xorg.conf file, the tricky part is the "Device" and "Protocol" parameters. Use the above output (in my case, event5) as the value for "Device", and "event" as the value for "Protocol". Saved the file, restart and the Alps on Sony works again.

The following is my xorg.conf:

[FONT="Fixedsys"]
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection 

Section "InputDevice"
        Identifier      "ALPS"
        Driver          "synaptics"
        Option          "AlwaysCore"
        Option          "Device"                "/dev/input/event5"
        Option          "Protocol"              "event"
        Option          "LeftEdge"              "120"
        Option          "RightEdge"             "830"
        Option          "TopEdge"               "120"
        Option          "BottomEdge"            "650"
        Option          "FingerLow"             "14"
        Option          "FingerHigh"            "15"
        Option          "MaxTapTime"            "180"
        Option          "MaxTapMove"            "110"
        Option          "ClickTime"             "0"
        Option          "EmulateMidButtonTime"  "75"
        Option          "VertScrollDelta"       "10"
        Option          "HorizScrollDelta"      "0"
        Option          "MinSpeed"              "0.45"
        Option          "MaxSpeed"              "0.75"
        Option          "AccelFactor"           "0.020"
        Option          "EdgeMotionMinSpeed"    "200"
        Option          "EdgeMotionMaxSpeed"    "200"
        Option          "UpDownScrolling"       "1"
        Option          "CircularScrolling"     "0"
        Option          "CircScrollDelta"       "0.1"
        Option          "CircScrollTrigger"     "2"
        Option          "SHMConfig"             "true"
EndSection

......

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "ALPS"
EndSection

[/FONT]


Hope this will help.

---

### Post by jrbj on 2005-10-20
I used your instructions to sucessfully disable "Tapping" on the touchpad of my Toshiba M35X-S111.

My original xorg.conf showed that the trackpad was being detected incorrectly. I **knew** it was an ALPS touchpad, but it wasn't showing up as one.

I'm so glad I was finally able to turn off Tapping. Accidentally clicking links and menu items was driving me crazy.

---

### Post by GoodPanos on 2005-10-21
I followed your recommendations and my came up as follows after I entered the command,  *cat /proc/bus/input/devices*:
**N: Name="PS/2 Mouse"**
**H: Handlers=mouse0 event1 ts0**

I couldn't find one for the AlpsPS/2.  So I made the changes accordingly into the xorg.conf.  Rebooted and the same thing, no scrolling.

Then just for the heck of it I issued command *cat /proc/bus/input/devices* and this time I noticed there was an AlpsPS/2 section.  Now, it was "event2".  So made the corrections and reboot and still the same ol'thing, no scrolling.

Any ideas as to what's going on?

---

### Post by jrbj on 2005-10-21
[QUOTE=GoodPanos]I followed your recommendations and my came up as follows after I entered the command,  *cat /proc/bus/input/devices*:
**N: Name="PS/2 Mouse"**
**H: Handlers=mouse0 event1 ts0**

I couldn't find one for the AlpsPS/2.  So I made the changes accordingly into the xorg.conf.  Rebooted and the same thing, no scrolling.

Then just for the heck of it I issued command *cat /proc/bus/input/devices* and this time I noticed there was an AlpsPS/2 section.  Now, it was "event2".  So made the corrections and reboot and still the same ol'thing, no scrolling.

Any ideas as to what's going on?[/QUOTE]

Can you post the output from **cat /proc/bus/input/devices** and your xorg.config file?

---

### Post by GoodPanos on 2005-10-21
The output of *cat /proc/bus/input/devices* is as follows:
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=1 80000004 2000000 3002078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="PS/2 Mouse"
P: Phys=isa0060/serio1/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse1 event2 ts1
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
H: Handlers=kbd event3
B: EV=40001
B: SND=6

And the xorg.conf is:

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
	Identifier	"ALPS"
	Driver		"synaptics"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/event2"	
# Option		"Device"		"/dev/psaux"
# Option		"Device"		"/dev/input/mice"
# Option		"Protocol"		"auto-dev"
	Option		"Protocol"		"event"
	Option		"LeftEdge"		"120"
	Option		"RightEdge"		"830"
	Option		"TopEdge"		"120"
	Option		"BottomEdge"		"650"
	Option		"FingerLow"		"14"
	Option		"FingerHigh"		"15"
	Option		"MaxTapTime"		"180"
	Option		"MaxTapMove"		"110"
	Option		"ClickTime"		"0"
	Option		"EmulateMidButtonTime"	"75"
	Option		"VertScrollDelta"	"10"
	Option		"HorizScrollDelta"	"10"
	Option		"MinSpeed"		"0.45"
	Option		"MaxSpeed"		"0.75"
	Option		"AccelFactor"		"0.020"
	Option		"EdgeMotionMinSpeed"	"200"
	Option		"EdgeMotionMaxSpeed"	"200"
	Option		"UpDownScrolling"	"1"
	Option		"CircularScrolling"	"0"
	Option		"CircScrollDelta"	"0.1"
	Option		"CircScrollTrigger"	"2"
	Option		"SHMConfig"		"true"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M300 (M22)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M300 (M22)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1440x900" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1440x900" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1440x900" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1440x900" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1440x900" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1440x900" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"ALPS"
EndSection

Section "DRI"
	Mode	0666
EndSection

My laptop is a Dell Inspiron 6000

---

### Post by perlhead on 2005-10-21
I'm at  wit's ends trying to get the ALPS on my HP Pavilion dv4000 to work.

The weird thing is that the driver seems to detect, initialize and configure the touchpad... yet I still don't get any of the touchpad's features (i.e. it works as a really annoying mouse, but no scrolling, dragging, multiple-tapping or anything like that). The relevant section of X.org's logfile looks encouraging:

(II) Synaptics touchpad driver version 0.13.6
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event1
(**) Option "Device" "/dev/input/event1"
(**) Option "SHMConfig" "True"
(**) Option "LeftEdge" "130"
(**) Option "RightEdge" "840"
(**) Option "TopEdge" "130"
(**) Option "BottomEdge" "640"
(**) Option "FingerLow" "7"
(**) Option "FingerHigh" "8"
(**) Option "MaxTapTime" "180"
(**) Option "MaxTapMove" "110"
(**) Option "EmulateMidButtonTime" "75"
(**) Option "VertScrollDelta" "20"
(**) Option "HorizScrollDelta" "20"
(**) Option "EdgeMotionMinSpeed" "200"
(**) Option "EdgeMotionMaxSpeed" "200"
(**) Option "UpDownScrolling" "1"
(**) Option "TapButton1" "1"
(**) Option "TapButton2" "2"
(**) Option "TapButton3" "3"
(**) Option "CircularScrolling" "1"
(**) Option "CircScrollTrigger" "2"
(--) Synaptics Touchpad ALPS touchpad found
(**) Option "AlwaysCore" "True"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad ALPS touchpad found

This is for the follwing configuration, which is an aggregate of stuff I found googling for a solution:

Section "InputDevice"
    Driver  	    "synaptics"
    Identifier      "Synaptics Touchpad"
    Option          "AlwaysCore"                "True"
    Option          "SendCoreEvents"            "True"
    Option          "SHMConfig"                 "True"
#    Option          "DevPhys"                   "isa0060/serio4/input0"
#    Option          "Device"                    "/dev/input/mouse1"
    Option          "Device"                    "/dev/input/event2"
    Option          "Protocol"                  "auto-dev"
    Option          "LeftEdge"                  "130"
    Option          "RightEdge"                 "840"
    Option          "TopEdge"                   "130"
    Option          "BottomEdge"                "640"
    Option          "FingerLow"                 "7"
    Option          "FingerHigh"                "8"
    Option          "MaxTapTime"                "180"
    Option          "MaxTapMove"                "110"
    Option          "EmulateMidButtonTime"      "75"
    Option          "VertScrollDelta"           "20"
    Option          "HorizScrollDelta"          "20"
    Option          "MinSpeed"                  "0.60"
    Option          "MaxSpeed"                  "1.10"
    Option          "AccelFactor"               "0.030"
    Option          "EdgeMotionMinSpeed"        "200"
    Option          "EdgeMotionMaxSpeed"        "200"
    Option          "UpDownScrolling"           "1"
    Option          "CircularScrolling"         "1"
    Option          "CircScrollDelta"           "0.1"
    Option          "CircScrollTrigger"         "2"
    Option          "SHMConfig"                 "on"
    Option          "Emulate3Buttons"           "on"
    Option          "TapButton1"                "1"
    Option          "TapButton2"                "2"
    Option          "TapButton3"                "3"
    Option          "LockedDrops"               "1"
EndSection

And this is how /proc/bus/input/devices reports the device

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio4/input0
H: Handlers=mouse1 event2 ts1
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

Am I doing anything reaaaaaaly stupid? Any ideas?

---

### Post by jrbj on 2005-10-21
[QUOTE=GoodPanos]...
snip log
...

My laptop is a Dell Inspiron 6000[/QUOTE]

The xorg.config looks good to me.  But I may have missed something that someone else might notice.

---

### Post by jrbj on 2005-10-21
[QUOTE=perlhead]I'm at  wit's ends trying to get the ALPS on my HP Pavilion dv4000 to work.

...
...
Section "InputDevice"
Driver  	    "synaptics"
Identifier "Synaptics Touchpad"
Option          "AlwaysCore"                "True"
Option          "SendCoreEvents"            "True"
Option          "SHMConfig"                 "True"
#    Option          "DevPhys"                   "isa0060/serio4/input0"
#    Option          "Device"                    "/dev/input/mouse1"
Option "Device" "/dev/input/event2"
Option "Protocol" "auto-dev"
...

EndSection

And this is how /proc/bus/input/devices reports the device

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio4/input0
H: Handlers=mouse1 event2 ts1
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

Am I doing anything reaaaaaaly stupid? Any ideas?[/QUOTE]


Try the following changes in bold in the InputDevice section for the trackpad:

Section "InputDevice"
Driver  	    "synaptics"
Identifier      "**ALPS**"
Option          "AlwaysCore"                "True"
Option          "SendCoreEvents"            "True"
Option          "SHMConfig"                 "True"
#    Option          "DevPhys"                   "isa0060/serio4/input0"
#    Option          "Device"                    "/dev/input/mouse1"
Option          "Device"                    "/dev/input/event2"
Option          "Protocol"                  "**event**"


Also at the end of the xorg.config file, in the server layout section, make sure it specifies ALPS for the input device

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice **"ALPS"**
EndSection

---

### Post by apu95 on 2005-10-21
[QUOTE=perlhead]I'm at  wit's ends trying to get the ALPS on my HP Pavilion dv4000 to work.

The weird thing is that the driver seems to detect, initialize and configure the touchpad... yet I still don't get any of the touchpad's features (i.e. it works as a really annoying mouse, but no scrolling, dragging, multiple-tapping or anything like that). The relevant section of X.org's logfile looks encouraging:

(II) Synaptics touchpad driver version 0.13.6
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event1
(**) Option "Device" "/dev/input/event1"
(**) Option "SHMConfig" "True"
(**) Option "LeftEdge" "130"
(**) Option "RightEdge" "840"
(**) Option "TopEdge" "130"
(**) Option "BottomEdge" "640"
(**) Option "FingerLow" "7"
(**) Option "FingerHigh" "8"
(**) Option "MaxTapTime" "180"
(**) Option "MaxTapMove" "110"
(**) Option "EmulateMidButtonTime" "75"
(**) Option "VertScrollDelta" "20"
(**) Option "HorizScrollDelta" "20"
(**) Option "EdgeMotionMinSpeed" "200"
(**) Option "EdgeMotionMaxSpeed" "200"
(**) Option "UpDownScrolling" "1"
(**) Option "TapButton1" "1"
(**) Option "TapButton2" "2"
(**) Option "TapButton3" "3"
(**) Option "CircularScrolling" "1"
(**) Option "CircScrollTrigger" "2"
(--) Synaptics Touchpad ALPS touchpad found
(**) Option "AlwaysCore" "True"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad ALPS touchpad found

This is for the follwing configuration, which is an aggregate of stuff I found googling for a solution:

Section "InputDevice"
    Driver  	    "synaptics"
    Identifier      "Synaptics Touchpad"
    Option          "AlwaysCore"                "True"
    Option          "SendCoreEvents"            "True"
    Option          "SHMConfig"                 "True"
#    Option          "DevPhys"                   "isa0060/serio4/input0"
#    Option          "Device"                    "/dev/input/mouse1"
    Option          "Device"                    "/dev/input/event2"
    Option          "Protocol"                  "auto-dev"
    Option          "LeftEdge"                  "130"
    Option          "RightEdge"                 "840"
    Option          "TopEdge"                   "130"
    Option          "BottomEdge"                "640"
    Option          "FingerLow"                 "7"
    Option          "FingerHigh"                "8"
    Option          "MaxTapTime"                "180"
    Option          "MaxTapMove"                "110"
    Option          "EmulateMidButtonTime"      "75"
    Option          "VertScrollDelta"           "20"
    Option          "HorizScrollDelta"          "20"
    Option          "MinSpeed"                  "0.60"
    Option          "MaxSpeed"                  "1.10"
    Option          "AccelFactor"               "0.030"
    Option          "EdgeMotionMinSpeed"        "200"
    Option          "EdgeMotionMaxSpeed"        "200"
    Option          "UpDownScrolling"           "1"
    Option          "CircularScrolling"         "1"
    Option          "CircScrollDelta"           "0.1"
    Option          "CircScrollTrigger"         "2"
    Option          "SHMConfig"                 "on"
    Option          "Emulate3Buttons"           "on"
    Option          "TapButton1"                "1"
    Option          "TapButton2"                "2"
    Option          "TapButton3"                "3"
    Option          "LockedDrops"               "1"
EndSection

And this is how /proc/bus/input/devices reports the device

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio4/input0
H: Handlers=mouse1 event2 ts1
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

Am I doing anything reaaaaaaly stupid? Any ideas?[/QUOTE]

Finally, someone with my same hardware! I have multi-tapping working though from the start, and I remember that I found a thread where it said how to enable dragging/dropping. I really want my scroll to work though...I'll try the stuff that was mentioned before.

---

### Post by GoodPanos on 2005-10-22
Same here.  Multi-tapping and drag-n-drop works fine for me except the scrolling.  I know it should work because it worked right of the back when I had Fedora Core 4 installed.

By the way which values in the xorg.conf file affect the sensitivity of the touchpad?

---

### Post by scubajeff on 2005-10-22
GoodPanos,

Could you please post your output of /var/log/Xorg.0.log, just the last 60 lines would be enough, so use the following command:

  tail -60 /var/log/Xorg.0.log

I need to be sure if your Alps touchpad is correctly config.

BTW, what is your machine's model?


scubajeff

---

### Post by GoodPanos on 2005-10-22
My notebook is a Dell Inspiron 6000 w/ Alps Touchpad and ATI X300.  Here's the output you requested:

(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 1052)
(II) RADEON(0): Largest offscreen area available: 1680 x 7136
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(II) RADEON(0): Direct rendering disabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(EE) No Input driver matching `synaptics'
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0

---

### Post by perlhead on 2005-10-22
[QUOTE=apu95]Finally, someone with my same hardware! I have multi-tapping working though from the start, and I remember that I found a thread where it said how to enable dragging/dropping. I really want my scroll to work though...I'll try the stuff that was mentioned before.[/QUOTE]

Well... nice to hear that it's possible. Would you mind please telling me what you did to at least get part of the functionality working?

---

### Post by perlhead on 2005-10-22
Thanks, but no change. In fact, changing the "Identifier" to "ALPS" doesn't do anybody any good: it's just a string to establish the connection between the device and the layout. For all X cares, it could read "WonderWartHog", as long as it had the same name in both places.

Changing the protcol to "event" might have worked (actually, I have failed finding any docs on the "auto-dev" protocol I had there in the first place). Unfortunately, it didn't change anything.

---

### Post by GoodPanos on 2005-10-23
So, any more thoughts on this?

---

### Post by chris86wm on 2005-10-23
i also have an inspiron 6000, so i am waiting for a fix.

---

### Post by scubajeff on 2005-10-23
GoodPanos,

From the output of your Xorg.0.log, it said:

....
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
**(EE) No Input driver matching `synaptics'**
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
......

Seems to me that means you don't even have your synaptics drivers being loaded. Please see if the file synaptics.o exists in the directory /usr/X11R6/lib/modules/input

If not, you might not even have the synaptics driver installed. Then you should do the following:
  sudo apt-get install xorg-driver-synaptics

After a successful installation, if you're using Breezy, reboot. If you are still using Hoary, you should add the following line in the "Module" session of your /etc/X11/xorg.conf and then reboot.

  Load       "synaptics"

---

### Post by perlhead on 2005-10-24
[QUOTE=perlhead]Changing the protcol to "event" might have worked (actually, I have failed finding any docs on the "auto-dev" protocol I had there in the first place). Unfortunately, it didn't change anything.[/QUOTE]

Sorry, this was my mistake. Changing the protocol to "event" instead of "auto-dev" did help. Now My ALPS can do tapping and scrolling. But for some reason it doesn't do drag or multi-tap.

Are there any diagnostics troubleshooting tools for this kind of problem?

---

### Post by bryan986 on 2005-10-24
For horizontal scrolling...

Make sure the boundaries of your touchpad are configured correctly, to make sure that there is room for the horizontal scroll portion

Check that
```

   Option "LeftEdge"                   "120"
   Option "RightEdge"                  "830"
   Option "TopEdge"                    "120"
   Option "BottomEdge"                 "550"

```
Adjust the edges as needed to make sure that the pointing area does not overlap the scrolling area

Check that
```

Option "HorizScrollDelta"           "20"

```
(other values besides 20 probably work)

Check that
```

Option "LeftRightScrolling"	       "1"

```

To get firefox to horizontally scroll instead of going forward/back, open the about:config page and
switch "mousewheel.horizscroll.withnokey.action" to 0

---

### Post by GoodPanos on 2005-10-24
Ok.  I did *sudo apt-get install xorg-driver-synaptics* and I get the following:
[B]Reading package lists... Done
Building dependency tree... Done
xorg-driver-synaptics is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/B]

Rebooted anyways and the same thing, no scrolling.  Do I have to add * Load "synaptics"* in my xorg.conf file even though I have Ubuntu 5.10?

Any other insights?  I've just about tried everything.

---

### Post by scubajeff on 2005-10-24
GoodPanos,

If you are sure the file "synaptics_drv.o" exists in the directory /usr/X11R6/lib/modules/input, then try adding the line Load "synaptics" in your xorg.conf.

---

### Post by GoodPanos on 2005-10-25
The command *sudo apt-get install xorg-driver-synaptics* does not create any *synaptics_drv.o* file.  I had to download this file from some forum and manually put it in the specified directory.   But even with that file, the scrolling still doesn't work.  As a matter of fact the touchpad just stops functioning.

Doing *sudo apt-get install xorg-driver-synaptics*, is that suppose to create a *synaptics_drv.o* file?

---

### Post by bryan986 on 2005-10-25
Chances are you need the 0.14.3 driver instead of the 0.13.6 in the repository, but that is more complicated

There is a topic around here somewhere that says where to get it, how to patch  it, and how to install it, I will try to find it

---

### Post by scubajeff on 2005-10-25
GoodPanos,

According to what you saw when you tried to install the "xorg-driver-synaptics" package, you should already have it installed. But then there is no synaptics_drv.o file, this is weird!

So what I now suggest is to remove and re-install the pacakge. Try these:

sudo apt-get remove xorg-driver-synaptics
sudo apt-get install xorg-driver-synaptics

BTW, is your Breezy a fresh install or an upgrade?

---

### Post by fgosse on 2005-10-26
Hi,
I've read this post with attention because i'm inspiron 6000 user too.
I've configured xorg.conf with succes (scrolling bar, double tap, drag and drop) But when i reboot, the modifications don't working. I must restart gdm (/etc/init.d/gdm restart) to use the touchpad with all fonctionnality.

Any ideas ?

Thanks
F.G

---

### Post by GoodPanos on 2005-10-26
So close but yet so far away.

Well, I removed the driver and reinstalled it.  Low and behold the synaptics_drv.o got installed.  Did  *cat /proc/bus/input/devices* and found out Device was event2.  Made the changes in the xorg.conf file rebooted...and the touchpad did not work at all.  Then added the "Load synaptics" line in the xorg.conf file and the same thing.

Changed the xorg.conf file back to the default settings...and got the touchpad working again but still no scrolling.

This is a fresh install of 5.10 Breezy.

---

### Post by barranco on 2005-10-26
Followed this instructions and Worked like a Charm

I had previously tapping and draggin but I wanted scrolling, now its scrolls too.

Toshiba M30X
ATI Mobility 9600 128mb
Atheros Wifi
Breezy 5.10

PS: Is there a good utility to configure my alps specific functions? I think it scrolls a little weeble too fast

---

### Post by scubajeff on 2005-10-26
GoodPanos,

Breezy support Synaptics/Alps touchpad out of box with the "psmouse" driver, so if you use the default xorg.conf setting, it will support most of the touchpad features except scrolling.

Since you have the synaptics_drv.o file installed, then as what I have mentioned in this thread before, please check the X11 log file, e.g. /var/log/Xorg.0.log, to see if any information there saying the synaptics driver has successfully found and setup the touchpad hardware. If not, you can still find some error message there to help out the diagnosis.

---

### Post by scubajeff on 2005-10-26
barranco,

use the tools come with the driver, call synclient. Make sure you have "SHMConfig" set to "on" in your xorg.conf to have this utility working. As for your problem, the parameter you should tune is "VertScrollDelta". Or if you hate the command line, just install the package "qsynaptics" to have nice Qt base configuration tool.

---

### Post by GoodPanos on 2005-10-26
Ran the *tail -60 /var/log/Xorg.0.log* command and found out that the version of the Synaptics driver is 0.13.6.  Is that the correct version to have?

All of you that have gotten the scrolling working what version do you have?

---

### Post by scubajeff on 2005-10-26
GoodPanos,

Both 0.14.3 and 0.13.6 works on my Sony Vaio TR2. I use version 0.14.3 right now.

Did you find anything useful in the log?

---

### Post by scubajeff on 2005-10-28
By the way, I have to set another option for the dragging works on my Sony Vaio TR2, which is:

Option          "GuestMouseOff"         "0"

---

### Post by 23meg on 2005-10-28
[QUOTE=scubajeff]By the way, I have to set another option for the dragging works on my Sony Vaio TR2, which is:

Option          "GuestMouseOff"         "0"[/QUOTE]

That option enabled tap and drag on my Toshiba Tecra M4 as well. Thanks a lot, I've been looking to fix this for a while.

---

### Post by remy the stampede on 2005-10-28
I followed the original posters instructions, and it enabled scrolling on my Inspiron 6000 as well as fixing the accidental clicking while browsing.  Thanks a lot!

---

### Post by Soilman on 2005-10-29
Try changing Option "CorePointer"
to Option "AlwaysCore"

[INDENT]Section "InputDevice"
	Identifier	"ALPS"
	Driver		"synaptics"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/event2"	
# Option		"Device"		"/dev/psaux"
# Option		"Device"		"/dev/input/mice"
# Option		"Protocol"		"auto-dev"
	Option		"Protocol"		"event"
	Option		"LeftEdge"		"120"
	Option		"RightEdge"		"830"
	Option		"TopEdge"		"120"
	Option		"BottomEdge"		"650"
	Option		"FingerLow"		"14"
	Option		"FingerHigh"		"15"
	Option		"MaxTapTime"		"180"
	Option		"MaxTapMove"		"110"
	Option		"ClickTime"		"0"
	Option		"EmulateMidButtonTime"	"75"
	Option		"VertScrollDelta"	"10"
	Option		"HorizScrollDelta"	"10"
	Option		"MinSpeed"		"0.45"
	Option		"MaxSpeed"		"0.75"
	Option		"AccelFactor"		"0.020"
	Option		"EdgeMotionMinSpeed"	"200"
	Option		"EdgeMotionMaxSpeed"	"200"
	Option		"UpDownScrolling"	"1"
	Option		"CircularScrolling"	"0"
	Option		"CircScrollDelta"	"0.1"
	Option		"CircScrollTrigger"	"2"
	Option		"SHMConfig"		"true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"ALPS"
EndSection

My laptop is a Dell Inspiron 6000[/QUOTE]
[/INDENT]

---

### Post by Soilman on 2005-10-29
[FONT="Garamond"][B]Got one for ya'all.
touchpad's only functionality is scrolling the focus window with up and down with verticle finger drag, change web pages with left and right (horizontal) finger drag, and pastes with tap.
What's up? How to fix this?
[/B][/FONT]
```

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse2 ts1 event4
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

```
From xorg.config

```
Section "InputDevice"
	Identifier "ALPS"
	Driver "synaptics"
	Option "AlwaysCore"
	Option "Device" "/dev/input/event4"
	Option "Protocol" "event"
	Option "LeftEdge" "120"
	Option "RightEdge" "830"
	Option "TopEdge" "120"
	Option "BottomEdge" "650"
	Option "FingerLow" "14"
	Option "FingerHigh" "15"
	Option "MaxTapTime" "180"
	Option "MaxTapMove" "110"
	Option "ClickTime"  "0"
	Option "EmulateMidButtonTime" "75"
	Option "VertScrollDelta" "10"
	Option "HorizScrollDelta" "0"
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
	Option "Emulate3Buttons" "on"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device" "/dev/input/mice"
	Option		"Protocol" "ImPS/2"
	Option		"Emulate3Buttons" "true"
	Option		"ZAxisMapping" "4 5"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"ALPS"
	InputDevice	"Configured Mouse"
EndSection
```

From end of Xorg.0.log

```
(II) Synaptics touchpad driver version 0.14.3
(**) Option "Device" "/dev/input/event4"
(**) Option "SHMConfig" "true"
(**) Option "LeftEdge" "130"
(**) Option "RightEdge" "840"
(**) Option "TopEdge" "130"
(**) Option "BottomEdge" "640"
(**) Option "FingerLow" "7"
(**) Option "FingerHigh" "8"
(**) Option "MaxTapTime" "180"
(**) Option "MaxTapMove" "110"
(**) Option "ClickTime" "0"
(**) Option "EmulateMidButtonTime" "75"
(**) Option "VertScrollDelta" "20"
(**) Option "HorizScrollDelta" "20"
(**) Option "EdgeMotionMinSpeed" "200"
(**) Option "EdgeMotionMaxSpeed" "200"
(**) Option "UpDownScrolling" "1"
(**) Option "CircularScrolling" "1"
(**) Option "CircScrollTrigger" "2"
(--) ALPS touchpad found
(**) Option "AlwaysCore"
(**) ALPS: always reports core events
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "ALPS" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
(--) ALPS touchpad found
(II) Configured Mouse: ps2EnableDataReporting: succeeded
```

---

### Post by theclaw on 2005-10-29
Thanks. This worked great. I can scroll again! [img]http://img365.imageshack.us/img365/5830/emotglomp2tc.gif[/img]

---

### Post by Sunnz on 2005-10-29
I tried to follow the instructions but my /proc/bus/input/devices only have these:
```
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=1 8000b004 42100000 3002178 f840d201 f2ffffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio4/input0
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3
```
I tried to have "Device" set to /dev/input/event1, and it didn't change anything...

---

### Post by Soilman on 2005-10-29
[QUOTE=Soilman][FONT="Garamond"][B]Got one for ya'all.
touchpad's only functionality is scrolling the focus window with up and down with verticle finger drag, change web pages with left and right (horizontal) finger drag, and pastes with tap.
What's up? How to fix this?
[/B][/FONT]

[CODE]Section "InputDevice"
	Identifier "ALPS"
	Driver "synaptics"
	Option "AlwaysCore"
	Option "Device" "/dev/input/event4"
	Option "Protocol" "event"
	Option "LeftEdge" "120"
	Option "RightEdge" "830"
	Option "TopEdge" "120"
	Option "BottomEdge" "650"
	Option "FingerLow" "14"
	Option "FingerHigh" "15"
	Option "MaxTapTime" "180"
	Option "MaxTapMove" "110"
	Option "ClickTime"  "0"
	Option "EmulateMidButtonTime" "75"
	Option "VertScrollDelta" "10"
	Option "HorizScrollDelta" "0"
	Option "MinSpeed" "0.45"
	Option "MaxSpeed" "0.75"
	Option "AccelFactor" "0.020"
	Option "EdgeMotionMinSpeed" "200"
	Option "EdgeMotionMaxSpeed" "200"
	Option "UpDownScrolling" "1"
	Option "CircularScrolling" "0"
	Option "CircScrollDelta" "0.1"
	Option "CircScrollTrigger" "2"
	[B]#Option "SHMConfig" "true"
	#Option "Emulate3Buttons" "on"[/B]
EndSection[CODE]

after remarking the bold items as above the touchpad now functions. It is still to sensitive to inadvertant palm or thumb brushes though. 
I would welcome any advice on how to disable taps or palm proof this.

---

### Post by Soilman on 2005-10-29
[QUOTE=Sunnz]I tried to follow the instructions but my /proc/bus/input/devices only have these:
```
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=1 8000b004 42100000 3002178 f840d201 f2ffffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio4/input0
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3
```
I tried to have "Device" set to /dev/input/event1, and it didn't change anything...[/QUOTE]

Did you check for psmouse.modprobe?
scubajeff  > First of all, if you have ever touched the file "/etc/modprobe.d/psmouse.modprobe", please remove it. Since it prevent the system from probing the Alps touchpad.
DiG

---

### Post by scubajeff on 2005-10-29
Soilman,

If you can't or don't bother to change those items in xorg.conf all by yourself. You can try to install those GUI synaptics touchpad configuration tools. Like qsynaptics, ksynaptic and gsynaptic. I'm using gsynaptic from: [http://gsynaptics.sourceforge.jp/](http://gsynaptics.sourceforge.jp/)

Don't worry, it's in English, and it will install a new item in your System->Preferrence menu. In fact, I found out the trick to turn on dragging using this tool. And i'm sure you can use it to fine tune the sensibility of your touchpad too.

---

### Post by Sunnz on 2005-10-29
[QUOTE=Soilman]Did you check for psmouse.modprobe?
scubajeff  
DiG[/QUOTE]
Yes I did checked it, that file wasn't there in the first place since I've never touched it.

---

### Post by gat on 2005-10-30
scubajeff -- thanks bro!!

I didn't see the output in the devices file, but I tried your xorg.conf changes anyway.  THEN I saw the changes and realized that, where you had "event5" I needed "event2".

I also set MaxTapTime to "0" (to turn off tapping) and I lowered your min and max speed settings by 0.10 (my fingers are obviously not as fast as yours).

My GUI config tools still don't seem to work, but I don't really care -- now that the xorg.conf file is good, the touchpad is behaving much better.

Thanks a lot, scubajeff

---

### Post by GoodPanos on 2005-10-31
AAAAAAAAAAAAAAAAAAAAAAHHHHHHHHH!!!!!
Finally, got the touchpad working!!!!

Well, I did have to reinstall Ubuntu.  I was running the preview release of 5.10.  Soon as I installed the latest version and followed the instructions here it worked right away.

Thank you very much for all your help and especially you **scubajeff**.

Now, who will have the honor to make a How To from A to Z on the Alps touchpad?

Is a How To just another post in this Forum or a special one?

---

### Post by ravv on 2005-10-31
I have a problem, i often use a USB mouse and that messes around with the eventX numbers. any way to solve it?

---

### Post by jjoyner on 2005-10-31
[QUOTE=ravv]I have a problem, i often use a USB mouse and that messes around with the eventX numbers. any way to solve it?[/QUOTE]

Same problem...I have no idea how to fix this.  $10 paypal to the first person to fix this issue...Let's start a pool to get the gurus minds runnin'....

$10 I say..:KS

---

### Post by GoodPanos on 2005-11-02
[QUOTE=ravv]I have a problem, i often use a USB mouse and that messes around with the eventX numbers. any way to solve it?[/QUOTE]
Run the *cat /proc/bus/input/devices* without the USB mouse plugged in.  What ever is the eventX, that is the one to use for your xorg.conf file.  Also make sure it's the one coming from the Alps driver i.e. "N: Name="AlpsPS/2 ALPS GlidePoint".

---

### Post by Soilman on 2005-11-02
I have ksynaptic installed. Not much help. I'll reinstall. If that is not the silver bulllet, I'll try uninstalling it and switch to another. 
Thanks to All & I will report back: I'm just a little busy with other fronts just now.

[QUOTE=scubajeff]Soilman,

If you can't or don't bother to change those items in xorg.conf all by yourself. You can try to install those GUI synaptics touchpad configuration tools. Like qsynaptics, ksynaptic and gsynaptic. I'm using gsynaptic from: [http://gsynaptics.sourceforge.jp/](http://gsynaptics.sourceforge.jp/)

Don't worry, it's in English, and it will install a new item in your System->Preferrence menu. In fact, I found out the trick to turn on dragging using this tool. And i'm sure you can use it to fine tune the sensibility of your touchpad too.[/QUOTE]

---

### Post by ravv on 2005-11-03
[QUOTE=GoodPanos]Run the *cat /proc/bus/input/devices* without the USB mouse plugged in.  What ever is the eventX, that is the one to use for your xorg.conf file.  Also make sure it's the one coming from the Alps driver i.e. "N: Name="AlpsPS/2 ALPS GlidePoint".[/QUOTE]


Yeah it works, until restart with/without. I don't want it to change around. I want it to stay the same or somehow link it to the new one. Can you include files/dynamic content in your xorg.conf?

---

### Post by scubajeff on 2005-11-04
After several hours research, I found the ultimate way to solve the dynamic eventX problem. Here it goes:

The reason why the eventX number changed is because "udev" control all the device naming during machine bootup. The way to get it fixed is to write our own udev rules. This is tricky! The very first thing to do is to identify the unique description of our Alps touchpad, type the following, substitute the "eventX" with your own number:

```
udevinfo -a -p `udevinfo -q path -n /dev/input/event5`
```

You will got something similar to this:

```
device '/sys/class/input/event5' has major:minor 13:69
  looking at class device '/sys/class/input/event5':
    SUBSYSTEM=="input"
    SYSFS{dev}=="13:69"

follow the "device"-link to the physical device:
  looking at the device chain at '/sys/devices/platform/i8042/serio0':
    BUS=="serio"
    ID=="serio0"
    DRIVER=="psmouse"
    SYSFS{bind_mode}=="auto"
    **SYSFS{description}=="i8042 Aux Port"**
    SYSFS{rate}=="100"
    SYSFS{resetafter}=="0"
    SYSFS{resolution}=="200"

  looking at the device chain at '/sys/devices/platform/i8042':
    BUS=="platform"
    ID=="i8042"
    DRIVER=="i8042"

  looking at the device chain at '/sys/devices/platform':
    BUS==""
    ID=="platform"
    DRIVER=="unknown"


```

The interested part of the out is highlighted.

Then creating our rule file: /etc/udev/alps.rules, with the SYSFS{description} part matching the output of udevinfo. You must use sudo to create it. File content:

```
BUS="serio", SYSFS{description}="i8042 Aux Port", KERNEL="event?", SYMLINK="input/alps"

```

Then create a link to this rule file at /etc/udev/rules.d directory

```
sudo ln -s /etc/udev/rules.d/40_alps.rules /etc/udev/alps.rules

```

The number 40 is to make sure it get loaded before the system-wide udev.rules file.
After the above setup, the machine, when bootup, will create a symbolic link /dev/input/alps to the correct eventX of our Alps touchpad. So we have to change our xorg.conf to reflect this change. If you follow this thread from the very begining, you should know the change is:

```
        Option          "Device"                "/dev/input/alps"

```

Ok, now reboot, and you will never miss your Alps again.

---

### Post by outdooricon on 2005-11-10
[QUOTE=scubajeff]
Then create a link to this rule file at /etc/udev/rules.d directory

```
sudo ln -s /etc/udev/rules.d/40_alps.rules /etc/udev/alps.rules

```
[/QUOTE]

I'd just like to offer my help in a correction to this for anyone directly copying and pasting like I did. The code should actually read: ```
sudo ln -s /etc/udev/alps.rules /etc/udev/rules.d/40_alps.rules

```

Thanks for all of your hard work on this scubajeff! I love using my touchpad now!

---

### Post by lol on 2005-11-14
Hi,

Does anybody knows what is the meaning of the values for the following options?

```
        Option          "LeftEdge"              "120"
        Option          "RightEdge"             "830"
        Option          "TopEdge"               "120"
        Option          "BottomEdge"            "650"
```

My touchpad is more or less working with those values, but I would like to understand them...

Thx in advance.

---

### Post by ispiked on 2005-11-15
[QUOTE=lol]Hi,
Does anybody knows what is the meaning of the values for the following options?
[/QUOTE]There is a nice little section on this in the README located in /usr/share/doc/xorg-driver-synaptics/.
```

The LeftEdge, RightEdge, TopEdge and BottomEdge parameters are used to
define the edge and corner areas of the touchpad. The parameters split
the touchpad area in 9 pieces, like this:

        LeftEdge  RightEdge
            v         v
            |         |       Physical top edge
          1 |    2    | 3
        -------------------   TopEdge
            |         |
         4  |    5    | 6
            |         |
        -------------------   BottomEdge
         7  |    8    | 9
            |         |       Physical bottom edge
        ^                 ^
     Physical          Physical
     left edge        right edge

Coordinates to the left of LeftEdge are part of the left edge (areas
1, 4 and 7), coordinates to the left of LeftEdge and above TopEdge
(area 1) are part of the upper left corner, etc. A good way to find
appropriate edge parameters is to enable the SHMConfig option and run
"synclient -m 1" to see the x/y coordinates corresponding to different
positions on the touchpad.
```

---

### Post by lol on 2005-11-16
> There is a nice little section on this in the README located in /usr/share/doc/xorg-driver-synaptics/.

Thanks, but I was able to find this much. In fact my question wasn't clear enough.
What I was looking for was the values that can be used for those options. I couldn't understand the fact that LeftEdge and TopEdge are always set to 120 in almost all examples on the net (I would set them to 0). I was also wondering how to find the maximum possible value (the coordinates of the bottom right corner).

Anyway I now have the answer. I just wasn't aware that after starting 'synclient -m 1', you can press the touchpad to get the coordinates of the corresponding position (I thought that the command was printing the maximum values immediatly, and I was always pressing ctrl-C after it displayed the first line...).

My mistake for not reading the doc properly.

---

### Post by Elv13 on 2005-11-19
Ok, my touch pad work but no multitapping (no clik lock or double clik inside 1 sec), no scroll
hardware:
Toshiba Satellite A70-TS1
Phoenix BIOS (never help for linux but it was working before)
512ram
60gb hdd
1280x800 screen

cat /proc/bus/input/devices output:
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
H: Handlers=kbd
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="PS/2 Mouse"
P: Phys=isa0060/serio4/input1
H: Handlers=mouse0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio4/input0
H: Handlers=mouse1
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003


XORG.conf :

```

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
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
	Option "AlwaysCore"	
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
	Option "HorizScrollDelta" "0"
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
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 U3 (R200 IGP)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Option "AGPMode" "4"
	Option "AGPFastWrite" "True"
	Option "EnablePageFlip" "True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9000 U3 (R200 IGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
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

its a gentoo mix with ubuntu mepis and FC4. I actually use gentoo but it was same with all distribution. Before 2.6.11, double click was working, but not anymore. Breezy use 2.6.12, Its why there is actually some problem with these touchpad, more than before... Any tips?

---

### Post by bigken on 2005-11-23
Hi & thx this worked  my inspiron 9200 :p 
no horizontal scrole ?

Section "InputDevice"
        Identifier      "Alps Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/event2"
        Option          "Protocol"              "event"
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
        Option "HorizScrollDelta" "0"
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


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Alps Touchpad"
EndSection

---

### Post by Dooglus on 2005-11-27
[QUOTE=bigken]
no horizontal scrole ?

        Option "HorizScrollDelta" "0"
EndSection[/QUOTE]

Setting HorizScrollDelta to 0 will result in no horizontal scrole.

---

### Post by TwiceOver on 2005-11-27
Thanks for all the work in this thread.  I noticed when I switched from Hoary to Breezy the Alps touchpad on my Toshiba A15 stopped working properly.  So far I have gotten everything back except click and drag... kinda.

Its odd, I can click and HIGHLIGHT text, which is probably more useful than anything else.  However, I cannot click and drag items (files, windows...)

I have made the proper changes to my xorg.conf and have also installed qsynaptics (which is an easy install and helps out the scroll speed and random taps) however no luck on the tap drag.

Here is the ALPS pointer section of my xorg.conf... Maybe I missed something?

EDIT:  **Fixed the problem**

I had to increase my MaxTapTime to 270 or above to fix the dragging.  Works Great now.  Thanks for the help.

```
 
Section "InputDevice"
	Identifier 	"ALPS"
	Driver 		"synaptics"
	Option 		"AlwaysCore"
	Option 		"Device" 		"/dev/input/event2"
	Option 		"Protocol" 		"event"
	Option 		"LeftEdge" 		"120"
	Option 		"RightEdge" 		"830"
	Option 		"TopEdge" 		"120"
	Option 		"BottomEdge" 		"650"
	Option 		"FingerLow" 		"14"
	Option 		"FingerHigh" 		"15"
	Option 		"MaxTapTime" 		"180"
	Option 		"MaxTapMove" 		"110"
	Option 		"ClickTime" 		"0"
	Option 		"EmulateMidButtonTime" 	"75"
	Option 		"VertScrollDelta" 	"10"
	Option 		"HorizScrollDelta" 	"0"
	Option 		"MinSpeed" 		"0.45"
	Option 		"MaxSpeed" 		"0.75"
	Option 		"AccelFactor" 		"0.020"
	Option 		"EdgeMotionMinSpeed" 	"200"
	Option 		"EdgeMotionMaxSpeed" 	"200"
	Option 		"UpDownScrolling" 	"1"
	Option 		"CircularScrolling" 	"0"
	Option 		"CircScrollDelta" 	"0.1"
	Option 		"CircScrollTrigger" 	"2"
	Option 		"SHMConfig" 		"on"
	Option 		"GuestMouseOff" 	"0"
	Option		"SHMConfig"		"on"
EndSection

```

---

### Post by bigken on 2005-11-27
[QUOTE=Dooglus]Setting HorizScrollDelta to 0 will result in no horizontal scrole.[/QUOTE]
cheers mate changed to 20 sorted:D

---

### Post by fezzik on 2005-11-30
I have a compaq R3440US.  It has an ALPS touchpad.  Mine seems to work fine except for scrolling.  I would really like scrolling.  I see all the instructions seem to change a whole bunch of other stuff.  I like the way mine taps and drags and does everything I just really would like the scrolling.   Is there anyway to do that with these directions without ruining everything else?

---

### Post by TwiceOver on 2005-11-30
[QUOTE=fezzik]I have a compaq R3440US.  It has an ALPS touchpad.  Mine seems to work fine except for scrolling.  I would really like scrolling.  I see all the instructions seem to change a whole bunch of other stuff.  I like the way mine taps and drags and does everything I just really would like the scrolling.   Is there anyway to do that with these directions without ruining everything else?[/QUOTE]

Make sure in /etc/X11/xorg.conf "UpDownScrolling" is set to "1".

---

### Post by fezzik on 2005-12-04
For some reason my  /etc/X11/xorg.conf says that it is a synaptic but all documentation and everything says that it is an ALPS touchpad.  What can I do about that? The horizontal scroll didn't help.

---

### Post by TwiceOver on 2005-12-04
[QUOTE=fezzik]For some reason my  /etc/X11/xorg.conf says that it is a synaptic but all documentation and everything says that it is an ALPS touchpad.  What can I do about that? The horizontal scroll didn't help.[/QUOTE]

Not sure exactly what to do about the scrolling but the pad will use the synaptics driver.  Mine is the same way.  

Sorry I am of no real help.  I know my scrolling didn't work at first but I can't even remember what I did.  I know it was something in this thread though...

---

### Post by fezzik on 2005-12-04
OK I followed all the directions on here and scrolling works, drag and drop works everything works great but I still have the sensitivity trouble with accidentally clicking on links as I move across pages.  I want to know what the clicktime "0" means what it does also what does circular scrolling do?  I made the MaxTapTime thing 270 I saw that that made the drag and drop work which it seemed to but I am thinking it could be affecting the accidental clicking thing.  Any ideas?

here is my Xorg.conf file.  Any suggestions?  I have big slow fingers I turn my pad off when I type using the on off button the only thing not doing what I want is the super sensitivity.  Wow this was about the last thing that was aggrivating about my switch to Linux.  I even found how to get into my work VPN.  That was impressive to me.  We need a better gui for that since it is like butter on Windows and like broccoli in Linux.  Anyway thanks for all the work on this and will love any suggestions.

Section "InputDevice"
Identifier "ALPS"
Driver "synaptics"
Option "AlwaysCore"
Option "Device" "/dev/input/event2"
Option "Protocol" "event"
Option "LeftEdge" "120"
Option "RightEdge" "830"
Option "TopEdge" "120"
Option "BottomEdge" "650"
Option "FingerLow" "14"
Option "FingerHigh" "15"
Option "MaxTapTime" "270"
Option "MaxTapMove" "110"
Option "ClickTime"  "0"
Option "EmulateMidButtonTime" "75"
Option "VertScrollDelta" "10"
Option "HorizScrollDelta" "20"
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

---

### Post by TwiceOver on 2005-12-04
Might just have to change a few settings that sound right.  For the longest time I couldn't get drag and drop to work until I finally adjusted the MaxTapTime at random.  

You can use the synclient command to adjust settings on the fly and see if it helps, however it does not permanently change the settings.  So after you have everything the way you want you need to make the changes to your xorg.conf.

I havn't had a lot of problems with random clicks but it does happen to me.  I set my clicktime to 100 and I'll report back on whether it helps.

---

### Post by Soilman on 2005-12-04
**Thanks again Scubajef!**
Wanted to follow on that the udev assignment was great!
After this assignment I installed ksynaptic (KUBUNTU) and went to "System Settings" and under hardware a new "Touchpad" icon is present.
I started the "Touchpad - System Settings".by double clicking.
Choose the ALPS option and adjust the touch pad borders (it's a pain but necessary on my T350).
Dissabled touchpad when typing, and made sure the Enable tapping box under Emulation is unchecked.
Now the touch pad will not respond to taps and the click buttons below the touchpad will be used insted.
No more cursor jumping around the screen while typing due to errant thumb or palm brushes.
Again, Capitol Improvement.

---

### Post by Crowhurst on 2005-12-04
THANKS! i just dropped this into my TR2's with 5.10 xorg.conf and it worked perfectly.

ScubaJeff, what did you do to your xorg.conf (or anything else) to get your 1280x768 screen resolution working? My xorg.conf shows the mode and display as 1280x768, but the resolution still comes up as 1024x768.

could you post the rest of your xorg.conf?

Thanks!

---

### Post by prizrak on 2005-12-04
Well it hates me, I run a Toshiba Satellite A10. Tried EVERYTHING in this thread, the modprobe file was removed, the xorg file was set to the exact specs as TwiceOver's (since it's also a Toshiba) well his/her settings are what I ended up with tried all the others. When I run the command "cat /proc/bus/input/devices" this is what I get
```
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=1 80000004 2000000 3002078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
H: Handlers=kbd event2
B: EV=40001
B: SND=6
```
The xorg log doesn't display any errors even though  it would seem that my mouse is set to be run on the PC Speaker event. Basically I'm lost, there was some command mentioned before that would probe the mouse or something to that effect and running it before I got some of the features working but now I can't find it. Oh and I'm running Breezy with Gnome, the Synaptics driver IS installed and I do have the needed .drv0 file. I will appreciate any suggestions.

---

### Post by fezzik on 2005-12-05
Prizrak did you restart after removing the modprob file?  It doesn't look like your computer is finding the ALPS driver.  That is the only way I have found to get it to look for another driver and do all the stuff it needs to do to get you something to mess with.  Then you can check the Event number and make it match the event of your ALPS driver. But your cat /proc/bus/input/devices doesn't seem to have the ALPS in it and it should show up after removing the modprob file and rebooting.

---

### Post by prizrak on 2005-12-06
[QUOTE=fezzik]Prizrak did you restart after removing the modprob file?  It doesn't look like your computer is finding the ALPS driver.  That is the only way I have found to get it to look for another driver and do all the stuff it needs to do to get you something to mess with.  Then you can check the Event number and make it match the event of your ALPS driver. But your cat /proc/bus/input/devices doesn't seem to have the ALPS in it and it should show up after removing the modprob file and rebooting.[/QUOTE]
Yep remove and reboot like it was supposed to be, driver installed from the repositories, when did the whole thing earlier managed to get the touchpad to be not super sensitive and have tap-to-drag working but no scrolling. I am quite baffled by this I kinda figured that my laptop is just the spawn of devil (which it very much is) and just plain refuses to let me use the touchpad in the way I want unless I run Windows with a very proprietary driver that actually installs real random services to run just so that I can use the functionality of the touchpad (god I hate Toshiba).

---

### Post by fezzik on 2005-12-06
Try changing the event in the xorg to event 1 that will get it to pull on the mouse event instead of the speaker event but that one is still showing the generic ps/2 mouse instead of the ALPS driver.  Mine did exactly what his did.  When I removed the mouse modprobe file and redid the cat /proc/bus/input/devices it showed the ALPS driver in the list.  When it did I used the event that displayed there for the ALPS driver and changed the info like he said.  Since I have gotten most of the other stuff set right.  Still a little sensitive but seems to work for me for the most part.  

I ended up setting the MaxTapTime to 250.  It gives me drag and drop with a little less sensitivity.  Anything lower than that and my big slow fingers don't get the drag and drop going anything more and everytime I stop or start I click on any available link or highlight all the text below.  So still playing.  It might be easier to figure out if I even halfway knew what these settings mean.  LOL.

---

### Post by fezzik on 2005-12-06
Just a thought I had that might get you going.  Change the xorg to use the "PS/2 Generic Mouse" on event2 since it doesn't look like the ALPS one is recognized even after removing the modprobe which I still find interesting.  But leave all the other settings like the ALPS xorg sections posted elsewhere.  That way the driver that your touchpad seems to be drawing from will be set to those settings.  I don't know but that is my creative idea.  Other than that if you have an external mouse hooked up to it you might try starting from the beginning without it hooked up.  It might be keeping your computer from recognizing it.  

Or Hopefully someone with more Linux experience and some knowlege in this area will offer some wisdom since mostly I can just guess at solutions that seem like they might work based on my limited knowlege and experience.

---

### Post by prizrak on 2005-12-06
Well I tried using event1 that did nothing, I have tried the Generic PS/2 mouse thing before I actually commented the entire section out to force X to use synaptics or to at least see which one it uses, no dice.

---

### Post by fezzik on 2005-12-07
Wow well I am out of guesses.  Sounds like you have tried everything I would have thought of.  Maybe someone more familiar with this kind of thing will jump in.  Good luck.

---

### Post by prizrak on 2005-12-07
[QUOTE=fezzik]Wow well I am out of guesses.  Sounds like you have tried everything I would have thought of.  Maybe someone more familiar with this kind of thing will jump in.  Good luck.[/QUOTE]
Hehe yeah pretty much, I accepted not being able to scroll. Thanks.

---

### Post by cpbl on 2005-12-19
Whee! Thanks, scubajeff! His procedure worked to get the touchpad doing nice things, including software scrolling, on my Toshiba Satellite 2410.  But  the laptop's hardware scrollwheel (which can also be pressed down as button 2; that function does still work ) is still not working and now it  is not even generating X events. That is, if I run "xev", the touchpad scrolling generates "button 4" and "button 5" events, but the scrollwheel generates nothing.  (even if I have a "zaxismapping" in xorg.conf).

How do I get the scrollwheel to work (like it does under other/past distributions) as well as the nice software scrolling on the right side of the touchpad? 


chris

---

### Post by manicka on 2005-12-29
I have added this howto to the Ubuntu Document Storage Facility

---

### Post by oberon on 2005-12-30
Just wanted to say thanks.  I finially got scrolling to function to work and decreased the sensitivity.  Great info!!

-oberon

---

### Post by prizrak on 2006-01-12
Out of the blue I have my scrolling working for some random reason installing SAMBA, disabling the firewall and restarting the laptop let it see the touchpad and the rest works pretty much as outlined...........

---

### Post by fezzik on 2006-01-25
Prizrak That is awesome.  I am glad to hear you finally got it working.  I knew there was a way to figure it out but sometimes I guess accidental stumbling on an answer is the best way to find some answers.  LOL.  I need to get back to reading up on stuff.  My Ubuntu is running smooth as can be right now so I don't even mess with it that much just get on and do what I do.

---

### Post by Griffin3 on 2006-02-01
Smashing good job, scubajeff! The stock Ubuntu install left the mouse miserably slow, and no scrolling area; near as I could tell, it was the most very generic synaptics support. Speeding up the mouse to the max in System->Preferences->Mouse made it just barely usable, but then when I clicked in the Parallels VM window it would revert to brain-damaging slowness. Applied your fix, and now the mouse is fast and happy everywhere, AND I get scroll areas as a bonus. Shiny!

---

### Post by Darts on 2006-03-09
Hi there!
Thanks to scubajeff & this topic I was able to make my ALPS touchpad working fine on my Laptop : Fujitsu Siemens Amilo A2000 (belgian type).
While fine tuning the settings in xorg.conf I found a page in google's cache explaining all the functions and I tought about sharing this ;)

```
Section "InputDevice"
        Driver          "synaptics"
        Identifier      "Touchpad"
	Option		"CorePointer"
        Option          "Device"        "/dev/input/event1"
        Option          "Protocol"      "auto-dev"
	# switch on/off shared memory for configuration
        Option          "SHMConfig"		"on"
	# coordinates of the edges
	Option		"LeftEdge"              "120"
	Option		"RightEdge"             "855"
	Option		"TopEdge"               "120"
	Option		"BottomEdge"            "650"
	# When finger pressure drops below this value,
	# the driver counts it as a release.
	Option		"FingerLow"             "14"
	# When finger pressure drops below this value,
	# the driver counts it as a release.
	Option		"FingerHigh"            "15"
	# max. time (in milliseconds) for detecting a tap
	Option		"MaxTapTime"            "180"
	# max. movement of the finger for detecting a tap
	Option		"MaxTapMove"            "110"
	# max. time (in milliseconds) for detecting a double tap
        Option          "MaxDoubleTapTime"      "100" #
	# the duration of the mouse click generated by tapping
        Option          "ClickTime"             "130" #
	# move distance of the finger for a scroll event
        Option          "VertScrollDelta"       "100"
        Option          "HorizScrollDelta"      "100"
	# finger pressure at which minimum edge motion speed is set
	Option		"EdgeMotionMinZ"   	"30"
	# finger pressure at which maximum edge motion speed is set
	Option		"EdgeMotionMaxZ"   	"100"
	# slowest setting for edge motion speed
	Option		"EdgeMotionMinSpeed"	"12"
	# fastest setting for edge motion speed
	Option		"EdgeMotionMaxSpeed"	"20"
	# If on, edge motion is also used for normal movements,
	# if off, egde motion is used only when dragging
	Option		"EdgeMotionUseAlways"	"off"
	# repeater device
        Option          "Repeater"      "/dev/input/event1"
	# min./max. speed factor
        Option          "MinSpeed"      "0.35" #
        Option          "MaxSpeed"      "1" #
	# acceleration factor
        Option          "AccelFactor"   "2.0" #
	# If on, the up/down buttons generate button 4/5 events.
	# If off, the up button generates a double click and
	# the down button generates a button 2 event.
        Option          "UpDownScrolling"       "on"
	# max time (in milliseconds) for middle button emulation.
        Option          "EmulateMidButtonTime"  "75"
	# If on, the Touchpad is switched off
	# (useful if an external mouse is connected)
	Option		"TouchpadOff"		"off"
	# switch on/off guest mouse (often a stick)
	Option		"GuestMouseOff"		"off
	# If off, a tap and drag gesture ends when you release the finger.
	# If on, the gesture is active until you tap a second time.
	Option	 	"LockedDrags"		"on"
	# Which mouse button is reported on a top corner tap
	# (RT right top, RB right bottom, LT left top, LB left bottom)
	# 0=No action, 1=Left Button, 2=Middle Button, 3=Right Button
        Option          "RTCornerButton"        "0"
        Option          "RBCornerButton"        "0"
        Option          "LTCornerButton"        "2"
        Option          "LBCornerButton"        "2"
	# Which mouse button is reported on a non-corner
	# (one|two|three)-finger tap.
	# 0=No action, 1=Left Button, 2=Middle Button, 3=Right Button
        Option          "TapButton1"            "1"
        Option          "TapButton2"            "2"
        Option          "TapButton3"            "3"
	# If on, circular scrolling is used (see below)
	Option		"CircularScrolling" 	"off"
	# Move angle (radians) of finger to generate a scroll event
	Option		"CircScrollDelta"  
	# Trigger region on the touchpad to start circular scrolling
	# 0=All Edges, 1=Top Edge, 2=Top Right Corner, 3=Right Edge, 4=Bottom Right Corner,
	# 5=Bottom Edge, 6=Bottom Left Corner, 7=Left Edge, 8=Top Left Corner
	Option		"CircScrollTrigger"
	# Instead of being a rectangle, the edge is the ellipse
	# enclosed by the Left/Right/Top/BottomEdge parameters.
	# For circular touchpads.
	Option	        "CircularPad"		"off"
EndSection
```

I hope this will help someone :)
FYI, I found it on [http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](this page) but in google's cache.

---

### Post by zalun on 2006-03-14
[QUOTE=Darts]
        Option          "Protocol"      "auto-dev"
[/QUOTE]

Please change the protocol to "event" it should work
remember to check address of your device by calling
```
cat /proc/bus/input/devices
```

Cheers

---

### Post by sn123 on 2006-03-16
First things first, I am a total noob when it comes to linux (just made a switch from Windows) so please go easy with your responses :).
Now to the problem: I am running Breezy (upgraded from Hoary) on a Dell Inspiron 600m and the touchpad doesn't wanna support the scrolling (tapping works though). I have tried almost everything that was mentioned in this thread without any luck :(, anyone got any ideas what I can do next? Here is the output from the files that I've seen people requesting :)

**$cat /proc/bus/input/devices**
```
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=1 80000004 2000000 3002078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
H: Handlers=kbd event2
B: EV=40001
B: SND=6
``` 
---------------------------
$ **tail -60 /var/log/Xorg.0.log**

```
 (**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) Synaptics touchpad driver version 0.13.6
(**) Option "Device" "/dev/input/event1"
(**) Option "SHMConfig" "on"
(**) Option "LeftEdge" "130"
(**) Option "RightEdge" "840"
(**) Option "TopEdge" "130"
(**) Option "BottomEdge" "640"
(**) Option "FingerLow" "7"
(**) Option "FingerHigh" "8"
(**) Option "MaxTapTime" "180"
(**) Option "MaxTapMove" "110"
(**) Option "EmulateMidButtonTime" "75"
(**) Option "VertScrollDelta" "20"
(**) Option "HorizScrollDelta" "20"
(**) Option "EdgeMotionMinSpeed" "200"
(**) Option "EdgeMotionMaxSpeed" "200"
(**) Option "UpDownScrolling" "1"
(**) Option "CircularScrolling" "1"
(**) Option "CircScrollTrigger" "2"
(**) Option "AlwaysCore"
(**) TouchPad: always reports core events
(WW) <default pointer>: No Device specified, looking for one...
(II) <default pointer>: Setting Device option to "/dev/psaux"
(--) <default pointer>: Device: "/dev/psaux"
(==) <default pointer>: Protocol: "Auto"
(**) Option "CorePointer"
(**) <default pointer>: Core Pointer
(==) <default pointer>: Emulate3Buttons, Emulate3Timeout: 50
(==) <default pointer>: Buttons: 3
(II) XINPUT: Adding extended input device "<default pointer>" (type: MOUSE)
(II) XINPUT: Adding extended input device "TouchPad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
(--) <default pointer>: PnP-detected protocol: "ExplorerPS/2"
(II) <default pointer>: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0

``` --------------------
and finally this is what my xorg.conf file looks like after nth revision:
```
 # If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
        #Load   "synaptics"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

#Section "InputDevice"
#       Identifier "Configured Mouse"
#       Driver "mouse"
#       Option "CorePointer"
#       Option "Device" "/dev/input/mice"
#       Option "Protocol" "ImPS/2"
#       Option "Emulate3Buttons" "true"
#       Option "ZAxisMapping" "4 5"
#EndSection

 Section "InputDevice"
   Driver "synaptics"
   Identifier "TouchPad"
   Option "AlwaysCore"
   Option "Device" "/dev/input/event1"
   Option "Protocol" "event"
   Option "LeftEdge" "130"
   Option "RightEdge" "840"
   Option "TopEdge" "130"
   Option "BottomEdge" "640"
   Option "FingerLow" "7"
   Option "FingerHigh" "8"
   Option "MaxTapTime" "180"
   Option "MaxTapMove" "110"
   Option "EmulateMidButtonTime" "75"
   Option "VertScrollDelta" "20"
   Option "HorizScrollDelta" "20"
   Option "MinSpeed" "0.60"
   Option "MaxSpeed" "1.10"
   Option "AccelFactor" "0.030"
   Option "EdgeMotionMinSpeed" "200"
   Option "EdgeMotionMaxSpeed" "200"
   Option "UpDownScrolling" "1"
   Option "CircularScrolling" "1"
   Option "CircScrollDelta" "0.1"
   Option "CircScrollTrigger" "2"
   Option "SHMConfig" "on"
   Option "Emulate3Buttons" "on"
 EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
#       InputDevice     "Configured Mouse"
        InputDevice     "TouchPad"
EndSection

``` 
TIA,
S

---

### Post by sn123 on 2006-03-18
bump...anyone?

---

### Post by Green_Star on 2006-03-25
My touch pad is working but touchpad scrolling is not working. I really going mad when ever i want to scroll pages. 

my devices addresses are...

```
:**~$  cat /proc/bus/input/devices**
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=1 80000004 2000000 3002078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="PS/2 Mouse"
P: Phys=isa0060/serio4/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio4/input0
H: Handlers=mouse1 event2 ts1
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
H: Handlers=kbd event3
B: EV=40001
B: SND=6

```

My Xconfig file is 

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc
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
	Load 	"synaptics"
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

#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
#	Option		"Protocol"		"auto-dev"
#	Option		"HorizScrollDelta"	"0"
#	Option 		"SHMConfig" 		"true"
#EndSection

Section "InputDevice"
	Driver        	"synaptics"
  	Identifier    	"Synaptics Touchpad"
  	Option        	"Device"        	"/dev/psaux"
	Option 		"AlwaysCore"
  	Option        	"Protocol"      	"event"
  	Option        	"LeftEdge"      	"1700"
  	Option        	"RightEdge"    		"5300"
  	Option        	"TopEdge"     		"1700"
  	Option        	"BottomEdge"    	"4200"
  	Option        	"FingerLow"     	"25"
  	Option        	"FingerHigh"    	"30"
  	Option        	"MaxTapTime"    	"180"
  	Option        	"MaxTapMove"    	"220"
  	Option        	"VertScrollDelta" 	"100"
  	Option        	"MinSpeed"      	"0.06"
  	Option        	"MaxSpeed"      	"0.12"
  	Option        	"AccelFactor" 		"0.0010"
  	Option       	"SHMConfig"     	"on"
#  	Option       	"Repeater"      	"/dev/ps2mouse"
EndSection



Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 (M6 LY)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9000 (M6 LY)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
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


when i give the following command the result is 

:~$ synclient -m 1
    time     x    y   z f  w  l r u d m     multi  gl gm gr gdx gdy
   0.000     0    0   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0


even i move the cursor using my touchpad nothing was changing in the above values. Please help me to resolve this issue.

**I read all this thread and tried all possibilities for almost a week, but i am not succeeded.**

Thanks in advance.



-------

---

### Post by Brightrock on 2006-03-28
I used the original posters advice and the scrolling works on my Dell 9300.  Got it to work just before my battery was out late last night.  I haven't experimented that much (still have to do some of my work in XP).  The mouse seemed to be moving too fast, but the vertical scrolling worked and it didn't seem to be as over sensitive as it was before.  Anyhow, just thought someone with my hardware might like to know.

---

### Post by Green_Star on 2006-04-10
[QUOTE=Green_Star]My touch pad is working but touchpad scrolling is not working. I really going mad when ever i want to scroll pages. 

my devices addresses are...

```
:**~$  cat /proc/bus/input/devices**
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=1 80000004 2000000 3002078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="PS/2 Mouse"
P: Phys=isa0060/serio4/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio4/input0
H: Handlers=mouse1 event2 ts1
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
H: Handlers=kbd event3
B: EV=40001
B: SND=6

```

My Xconfig file is 

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc
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
	Load 	"synaptics"
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

#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
#	Option		"Protocol"		"auto-dev"
#	Option		"HorizScrollDelta"	"0"
#	Option 		"SHMConfig" 		"true"
#EndSection

Section "InputDevice"
	Driver        	"synaptics"
  	Identifier    	"Synaptics Touchpad"
  	Option        	"Device"        	"/dev/psaux"
	Option 		"AlwaysCore"
  	Option        	"Protocol"      	"event"
  	Option        	"LeftEdge"      	"1700"
  	Option        	"RightEdge"    		"5300"
  	Option        	"TopEdge"     		"1700"
  	Option        	"BottomEdge"    	"4200"
  	Option        	"FingerLow"     	"25"
  	Option        	"FingerHigh"    	"30"
  	Option        	"MaxTapTime"    	"180"
  	Option        	"MaxTapMove"    	"220"
  	Option        	"VertScrollDelta" 	"100"
  	Option        	"MinSpeed"      	"0.06"
  	Option        	"MaxSpeed"      	"0.12"
  	Option        	"AccelFactor" 		"0.0010"
  	Option       	"SHMConfig"     	"on"
#  	Option       	"Repeater"      	"/dev/ps2mouse"
EndSection



Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 (M6 LY)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9000 (M6 LY)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
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


when i give the following command the result is 

:~$ synclient -m 1
    time     x    y   z f  w  l r u d m     multi  gl gm gr gdx gdy
   0.000     0    0   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0


even i move the cursor using my touchpad nothing was changing in the above values. Please help me to resolve this issue.

**I read all this thread and tried all possibilities for almost a week, but i am not succeeded.**

Thanks in advance.



-------[/QUOTE]

Can some one help me in this issue please.....

-
-
-

---

### Post by daageep on 2006-04-11
THANK YOU to the original author of this thread. I have gotten the touchpad on my Fujitsu S6120 working with vertical scrolling, dragging, etc. VERY HAPPY:D  camper. I am actually using Debian 2.6.15 kernel with fluxbox.

Note: for devices that are detected as an alps touchpad, you need kernel >2.6.11. i was running 2.6.10 this morning and could not get my alps touchpad detected at ALLL.

Greenstar, your device is set at /dev/psaux, but should be set to /dev/input/event2 (if i remember correctly). I am tempted to write a more comprehensive document on how to get everything working for my own reference. 8)

edit: also, it looks like your specified dimensions are wayyy too big. originally my dimensions were wayy too big such that my vertical scrolling did not work (bc the location of the vertical scroll was at the edge of the "big" touchpad i had). try to resize the touchpad to dimensions specified on the first page of the thread; that worked for me.

good luck

---

### Post by Green_Star on 2006-04-21
[QUOTE=daageep]THANK YOU to the original author of this thread. I have gotten the touchpad on my Fujitsu S6120 working with vertical scrolling, dragging, etc. VERY HAPPY:D  camper. I am actually using Debian 2.6.15 kernel with fluxbox.

Note: for devices that are detected as an alps touchpad, you need kernel >2.6.11. i was running 2.6.10 this morning and could not get my alps touchpad detected at ALLL.

Greenstar, your device is set at /dev/psaux, but should be set to /dev/input/event2 (if i remember correctly). I am tempted to write a more comprehensive document on how to get everything working for my own reference. 8)

edit: also, it looks like your specified dimensions are wayyy too big. originally my dimensions were wayy too big such that my vertical scrolling did not work (bc the location of the vertical scroll was at the edge of the "big" touchpad i had). try to resize the touchpad to dimensions specified on the first page of the thread; that worked for me.

good luck[/QUOTE]

[COLOR="Blue"]Thanks a bunch **daageep**, you made my day. It is working, you are the one.[/COLOR]

---

### Post by dieselpower on 2006-04-28
Wow, that was easy! I finaly got my touchpad working on my HP zv5000 in Gentoo! Thankyou!

---

### Post by DavidFourer on 2006-05-13
Help me turn off tap=click on Dell inspiron 6000 with possibly ALPS touchpad ????

My cat command produces

[COLOR="Blue"]I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="PS/2 Mouse"
P: Phys=isa0060/serio1/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse1 event2 ts1
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003
[/COLOR]
and my /etc/x11/xorg.config looks like
[COLOR="Blue"]Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection[/COLOR]

The 20 lines with "Identifier ALPS" are missing.  Should I ad them and change the end lines where it says:
[COLOR="Blue"]Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection[/COLOR]  to say InputDevice "ALPS"  
This is over my head, but I'd really like to get it working.
I just want to turn off "tap=click"
Thanks

---

### Post by acidphex on 2006-05-15
This worked great on my Sony PCG-Z1WA. Thanks a lot for posting this! I have one question though, is there a way I can make the veritcal scroll slower?

---

### Post by prym8 on 2006-05-17
Much thanks to the OP, not only did this work for me, the settings are just what I like ;).

For general information, this worked great for me on my **HP Pavilion zv5000 (specifically zv5495ca)**

m-

---

### Post by deleopario on 2006-05-23
I've been trying for ages to get my touchpad working, but even after reading everything in this thread it still is moving insanely slow and the scrolling doesn't work (though I did at least get it to stop tapping) and synconfig tells me I don't have a mouse set up with it despite my assigning the pad to it. I looked through the logs from bootup, it looked like the synaptic drivers did load but something went wrong I guess because one of the successful ones I think I saw in this thread was a lot longer (I'd copy and paste the log but I forget how to get to it). I've got a Presario R3210US, and this is my xconf.org:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/event2"
        Option          "Protocol"              "event"
        Option          "VertScrollDelta"      "20"
EndSection

Section "InputDevice"
        Driver          "synaptics"
        Identifier      "ALPS"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/event2"
        Option          "Protocol"              "event"
        Option "LeftEdge" "120"
        Option "RightEdge" "330"
        Option "TopEdge" "20"
        Option "BottomEdge" "150"
        Option "FingerLow" "1"
        Option "FingerHigh" "15"
        Option "MaxTapTime" "180"
        Option "MaxTapMove" "110"
        Option "ClickTime" "0"
        Option "EmulateMidButtonTime" "75"
        Option "VertScrollDelta" "40"
        Option "HorizScrollDelta" "20"
        Option "MinSpeed" "31.45"
        Option "MaxSpeed" "905.95"
        Option "AccelFactor" "8.50"
        Option "EdgeMotionMinSpeed" "230"
        Option "EdgeMotionMaxSpeed" "600"
        Option "UpDownScrolling" "1"
        Option "CircularScrolling" "0"
        Option "CircScrollDelta" "0.1"
        Option "CircScrollTrigger" "2"
        Option "SHMConfig" "true"
EndSection

```

---

### Post by DavidFourer on 2006-05-24
I have a computer for which none of the changes suggested here makes any difference (Dell inspiron 6000 and Breezy).  Fortunately my trackpad works acceptably.  What I find so frustrating about this thread is I don't understand the technology.  If I were fixing a short in a wire I would know how to trace it from one end of the circuit to the other.  Eventually I would know what was wrong, even if I couldn't fix it.   It's the same with the wireless

I found this:
Xorg.0.log:[COLOR="Green"]
Synaptics DeviceOn called
(--) **Synaptics Touchpad ALPS touchpad found**
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOff called
(WW) I810(0): Successfully set original devices
[/COLOR]

I also see where someone changed:
Option "Device" "/dev/input/event5" in Xorg.config
to:
....event2

Further down in the thread > You can try to install those GUI synaptics touchpad configuration tools. Like qsynaptics, ksynaptic and gsynaptic. I'm using gsynaptic from: [http://gsynaptics.sourceforge.jp/](http://gsynaptics.sourceforge.jp/)I will have to complile this :confused: --this is new to me.  

I'm thinking when Dapper is official June first I might try that and take it from there.

---

### Post by shane2peru on 2006-05-24
Ok, I have been working on my Toshiba laptop trying to get the scrolling feature to work.  My touchpad mouse does work, but doesn't scroll.  This is the main feature that I would like.  Here is my cat output:
```

cat /proc/bus/input/devices
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=1 80000004 2000000 3002078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="PS/2 Mouse"
P: Phys=isa0060/serio4/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio4/input0
H: Handlers=mouse1 event2 ts1
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003


```

Here is my xorg.conf

```

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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

```
 
Ok, one more this xorg.conf this one crashed my X and wouldn't let it start, I had to revert to my backup file!

```

##############################################################
#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
#	Option		"Protocol"		"auto-dev"
#	Option		"HorizScrollDelta"	"0"
#EndSection
###############################################################

Section "InputDevice"
Identifier "ALPS"
Driver "synaptics"
Option "AlwaysCore"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
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
Option "VertScrollDelta" "20"
Option "HorizScrollDelta" "0"
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

```
I'm using Breezy 5.10 up-to-date.

Any help would be greatly appreciated.  Thanks.

Shane

---

### Post by Morphius on 2006-06-02
If you are running dapper there is a known bug that will cause mouse issues for synaptic pads.

[https://launchpad.net/distros/ubuntu/+bug/47971](https://launchpad.net/distros/ubuntu/+bug/47971)

Check out the link for a work around.

---

### Post by morguns on 2006-06-13
Thanks much for this information. The touchpad on my Dell Inspiron 600m was painfully slow and y'all helped get it back into high gear. However, I can't get scrolling or tap and drag to work. I added these settings to xorg.conf, but all that did was slow the mouse down again.
[QUOTE=scubajeff]The following is my xorg.conf:
```

Section "InputDevice"
        Identifier      "ALPS"
        Driver          "synaptics"
        Option          "AlwaysCore"
        Option          "Device"                "/dev/input/event5"
        Option          "Protocol"              "event"
        Option          "LeftEdge"              "120"
        Option          "RightEdge"             "830"
        Option          "TopEdge"               "120"
        Option          "BottomEdge"            "650"
        Option          "FingerLow"             "14"
        Option          "FingerHigh"            "15"
        Option          "MaxTapTime"            "180"
        Option          "MaxTapMove"            "110"
        Option          "ClickTime"             "0"
        Option          "EmulateMidButtonTime"  "75"
        Option          "VertScrollDelta"       "10"
        Option          "HorizScrollDelta"      "0"
        Option          "MinSpeed"              "0.45"
        Option          "MaxSpeed"              "0.75"
        Option          "AccelFactor"           "0.020"
        Option          "EdgeMotionMinSpeed"    "200"
        Option          "EdgeMotionMaxSpeed"    "200"
        Option          "UpDownScrolling"       "1"
        Option          "CircularScrolling"     "0"
        Option          "CircScrollDelta"       "0.1"
        Option          "CircScrollTrigger"     "2"
        Option          "SHMConfig"             "true"
EndSection
```[/QUOTE]

Any advice on how to get the extra functionality from the touchpad? Here's the relevant portion of xorg.conf that at least gets the mouse working at a respectable speed:```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
#       Option          "Device"                "/dev/psaux"
#       Option          "Protocol"              "auto-dev"
        Option          "Device"                "/dev/input/event3"
        Option          "Protocol"              "event"
        Option          "HorizScrollDelta"      "0"
EndSection

```

---

### Post by morguns on 2006-08-08
about 1/2 the time my system boots up, the mouse settings don't take. is there a way to re-run the configuration settings at the command line? like ~/.bashrc will re-run if you make changes to it.

---

### Post by yanychar on 2006-09-06
> **TwiceOver said:**
> Thanks for all the work in this thread.  I noticed when I switched from Hoary to Breezy the Alps touchpad on my Toshiba A15 stopped working properly.  So far I have gotten everything back except click and drag... kinda.

EDIT:  **Fixed the problem**

I had to increase my MaxTapTime to 270 or above to fix the dragging.  Works Great now.  Thanks for the help.

```
 
Section "InputDevice"
	...
	Option 		"MaxTapTime" 		"270"
	...
EndSection

```

I have Sony TX770P, and this has worked for me. Thanks everyone.

---

### Post by iwalke on 2006-09-15
Hi i'm using a sony vaio vgn-fs215s... my computer is also recognising my ALPS touchpad as a "PS/2 Compatible Mouse" and I am unable to turn off 'tap-to-click' as far as I am aware. This is driving me crazy and i'm not really sure what to do, could someone describe to me (in layman's terms as far as possible) what to do?

thanks for any help :)

---

### Post by valica on 2006-12-27
apparently there are some modifications needed to use the "udev hack" in Edgy:

> **scubajeff said:**
> 
Then creating our rule file: /etc/udev/alps.rules, with the SYSFS{description} part matching the output of udevinfo. You must use sudo to create it. File content:

```
BUS="serio", SYSFS{description}="i8042 Aux Port", KERNEL="event?", SYMLINK="input/alps"

```


the syntax of udev rules changed in Edgy (see *man udev* for details), so the file */etc/udev/alps.rules* should contain:

```

$ cat /etc/udev/alps.rules 
BUS=="serio", SYSFS{description}=="i8042 Aux Port", KERNEL=="event?", SYMLINK+="input/alps"

```

> 
Then create a link to this rule file at /etc/udev/rules.d directory

```
sudo ln -s /etc/udev/rules.d/40_alps.rules /etc/udev/alps.rules

```

The number 40 is to make sure it get loaded before the system-wide udev.rules file.


following instructions in */etc/udev/rules.d/README* user created rules should begin with the number 50, so:

```

sudo ln -s /etc/udev/alps.rules /etc/udev/rules.d/50-alps.rules

```

now i have a static entry in /dev for my ALPS Touchpad... but i've been bitten by another bug :-k : [https://bugs.launchpad.net/distros/ubuntu/+source/xserver-xorg-input-synaptics/+bug/68540]("https://bugs.launchpad.net/distros/ubuntu/+source/xserver-xorg-input-synaptics/+bug/68540")

i hope this helps someone

---

### Post by anchois on 2007-03-30
Hello all, 

I have a Sony Vaio FS-315E with Edgy (upgraded from Dapper).
Only recently, I have upgraded my kernel and my touchpad wasn't recognized anymore (recognized as a PS2 mouse for most of the time).

I search a little and found that my touchpad is "moving" between the devices
/dev/input/event2 and /dev/input/event6

In xorg.conf, putting: 
Option          "Device"                "/dev/input/mouse1
doesn't work since the next line:
Option          "Protocol"             "auto-dev"
grab the first event device that seems to be a mouse (PS2 mouse, not the touchpad).

I make a quick and dirty hack to find at boot on which event device my touchpad is plugged:
```
ln -s /dev/input/`grep mouse1 /proc/bus/input/devices | cut -d " "  -f 3` /dev/input/alps
```
that makes a symbolic link to the correct /dev/input/event[1-6] to /dev/input/alps.

I put this line in /etc/rc.local to load at boot time and:
```
mv /etc/rc2.d/S99rc.local /etc/rc2.d/S12rc.local 
```
(so that it's starting before GDM and graphical session)

Then I put in /etc/X11/xorg.conf:
```
Option          "Device"                "/dev/input/alps"
Option          "Protocol"              "event"

```

It's seem to work fairly good ;)

---

### Post by effenberg0x0 on 2007-04-05
I was having problems with the ever changing Event[x] for the Alps and have sucessfully followed ScubaJeff's tip on getting myself a /dev/input/alps . If I cat it, I can see Touchpad output. 

My problem seems to be unique thou: When I start the PC and get into Ubuntu, the touchpad won't work, no matter what (and remember, I can log in and cat and see output on /dev/input/alps). Xorg.conf is ok, etc. 

The only way I have found to make it work is to kill "x-session-manager". Once I kill it, Ubuntu GUI goes down and up again, I get back to Ubuntu Graphical Login, and now the touchpad is working flawlessly and with all the advanced features, like scrolling, etc.

I am a newbie, but I am on this for days, loosing many hours on searchs and attempts to fix it. Does anyone has any idea what is going on here? 

Thanks,
Effenberg

---

### Post by effenberg0x0 on 2007-04-12
Hi guys, I still am having the same problem: When I start my notebook the touchpad is not working. If I restart X (ctrl+alt+backspace) then the touchpad starts working perfectly. I'm on that for more than a month... It's killing me. If anyone has any idea what I could do to solve this, please help, I don't know what else I can try...

Thanks,
Effenberg

---

### Post by Paul.Spectre on 2007-12-21
To all who put this thread together - Thanks! my Fujitsu Siemens Lifebook 6120 was about to part company with Gutsy because I couldn't get the scroll buttons / area working for many weeks, but you guys delivered the goods with your event-based hack. Have a good Xmas and a great life :)

---

