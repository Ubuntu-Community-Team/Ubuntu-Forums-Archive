---
title: "Compaq Presario R3000 - Nothing Works!"
date: 2005-06-12
forum: Hardware &amp; Laptops
---

### Post by Whitewolfe on 2005-06-12
This is getting ridiculous:

Ok I've got two major issues and I can't work them out.  I've been through the forums and through google in general, including Kinser's howto.  None of this stuff works and I can't figure out why.  Gotta be something simple but I am out of ideas.

Issue 1:  Synaptics Touchpad.

The system recongises the touchpad out of the box, no problem.  What IS a problem is that it does not seem to be possible to TURN OFF the dang tap thing.  I don't use it.  I don't want it.  I am sick of having to manually turn off the touchpad in order to be able to type without having the thing pick up false clicks when my thumb inadvertently touches the freaking pad.  I DID, through repeated studying of the results of Xorg.0.log, finally figure out how to make the system recongize the touchpad AS synaptics.  I've compiled the kernel with the alps patch.  I've edited xorg.conf until I become nauseous every time I see the words "sudo nano xorg.conf".  Nothing will turn off taps.  Maybe it's impossible, I don't know.  All I know is all the "this works fine for me" stuff doesn't.

Issue 2:  NVIDIA-glx

I can, through extensive trial and error, make the nvidia driver work.  X will start ok, I get the Nvidia logo, etc etc etc.  However, games like Neverwinter Nights and Enemy Territory don't work.  I get video but it's all garbled and seems to be "out of sync".  Again, all the "this xorg.conf works fine for me" stuff doesn't.

Anyone willing to help me figure this out, I would be happy to send info on any config files, etc that you like.   

The system is a Compaq Presario R3000 with the 15" wide screen.  I'm running Kubuntu Hoary.  

Tell me what else you want to know and I will be very happy to oblige and very grateful for any assistance.

-WW

Edited 06/11/05 - xorg.conf follows.   Note that comments in xorg.conf may not actually be relevant.  This .conf is bits and pieces of several others assembled through cut and paste.

```
# ************************************************** ********************
 # Refer to the xorg.conf(5) man page for details about the format of
 # this file.
 # ************************************************** ********************
 
 # ************************************************** ********************
 # Module section -- this section is used to specify
 # which dynamically loadable modules to load.
 # ************************************************** ********************
 #
 Section "Module"
 Load "GLcore"
 Load "synaptics"
 Load "bitmap"
 Load "dbe"
 Load "ddc"
 # Load "dri"
 Load "extmod"
 Load "freetype"
 Load "glx"
 Load "int10"
 Load "record"
 Load "speedo"
 Load "type1"
 Load "vbe"
 EndSection
 
 
 # ************************************************** ********************
 # Files section. This allows default font and rgb paths to be set
 # ************************************************** ********************
 
 Section "Files"
 FontPath "unix/:7100" # local font server
 # if the local font server has problems, we can fall back on these
 FontPath "/usr/lib/X11/fonts/misc"
 FontPath "/usr/lib/X11/fonts/cyrillic"
 FontPath "/usr/lib/X11/fonts/100dpi/:unscaled"
 FontPath "/usr/lib/X11/fonts/75dpi/:unscaled"
 FontPath "/usr/lib/X11/fonts/Type1"
 FontPath "/usr/lib/X11/fonts/CID"
 FontPath "/usr/lib/X11/fonts/Speedo"
 FontPath "/usr/lib/X11/fonts/100dpi"
 FontPath "/usr/lib/X11/fonts/75dpi"
 EndSection
 
 # ************************************************** ********************
 # Server flags section.
 # ************************************************** ********************
 
 Section "ServerFlags"
 
 # Uncomment this to cause a core dump at the spot where a signal is
 # received. This may leave the console in an unusable state, but may
 # provide a better stack trace in the core dump to aid in debugging
 
 # Option "NoTrapSignals"
 
 # Uncomment this to disable the <Crtl><Alt><Fn> VT switch sequence
 # (where n is 1 through 12). This allows clients to receive these key
 # events.
 
 # Option "DontVTSwitch"
 
 # Uncomment this to disable the <Crtl><Alt><BS> server abort sequence
 # This allows clients to receive this key event.
 
 # Option "DontZap"
 
 # Uncomment this to disable the <Crtl><Alt><KP_+>/<KP_-> mode switching
 # sequences. This allows clients to receive these key events.
 
 # Option "Dont Zoom"
 
 # Uncomment this to disable tuning with the xvidtune client. With
 # it the client can still run and fetch card and monitor attributes,
 # but it will not be allowed to change them. If it tries it will
 # receive a protocol error.
 
 # Option "DisableVidModeExtension"
 
 # Uncomment this to enable the use of a non-local xvidtune client.
 
 # Option "AllowNonLocalXvidtune"
 
 # Uncomment this to disable dynamically modifying the input device
 # (mouse and keyboard) settings.
 
 # Option "DisableModInDev"
 
 # Uncomment this to enable the use of a non-local client to
 # change the keyboard or mouse settings (currently only xset).
 
 # Option "AllowNonLocalModInDev"
 
 EndSection
 
 # ************************************************** ********************
 # Input devices
 # ************************************************** ********************
 
 # ************************************************** ********************
 # Core keyboard's InputDevice section
 # ************************************************** ********************
 
 Section "InputDevice"
 Identifier "Generic Keyboard"
 Driver "keyboard"
 Option "CoreKeyboard"
 Option "XkbRules" "xfree86"
 Option "XkbModel" "pc101"
 Option "XkbLayout" "en"
 EndSection
 
 
 # ************************************************** ********************
 # Core Pointer's InputDevice section
 # ************************************************** ********************
 
Section "InputDevice"
  	Driver  	"synaptics"
  	Identifier  	"Alps Touchpad"
	Option		"CorePointer"
  	Option		"Device"  		"/dev/input/event1"
  	Option		"Protocol"		"event"
  	Option		"LeftEdge"		"120"
  	Option		"RightEdge"		"960"
  	Option		"TopEdge"		"120"
  	#Option		"BottomEdge"		"650"
	# Prctically disables horizontal scroll (button 6 & 7)
	Option		"BottomEdge"		"800"
  	Option		"FingerLow"		"14"
  	Option		"FingerHigh"		"15"
  	Option		"MaxTapTime"		"0"
  	Option		"MaxTapMove"		"30"
  	Option		"EmulateMidButtonTime"	"75"
  	Option		"VertScrollDelta"	"20"
  	Option		"HorizScrollDelta"	"20"
  	Option		"MinSpeed"		"0.4"
  	Option		"MaxSpeed"		"1.1"
  	Option		"AccelFactor"		"0.015"
  	Option		"EdgeMotionMinSpeed"	"15"
  	Option		"EdgeMotionMaxSpeed"	"15"
  	Option		"UpDownScrolling"	"1"
  	Option		"CircularScrolling"	"0"
  	Option		"CircScrollDelta"	"0.1"
  	Option		"CircScrollTrigger"	"2"
	Option		"SHMConfig"		"on"
EndSection
 
 Section "InputDevice"
 Identifier "USB Mouse"
 Driver "mouse"
 Option "SendCoreEvents" "true"
 Option "Device" "/dev/input/mice"
 Option "Protocol" "ImPS/2"
 Option "Emulate3Buttons" "true"
 Option "ZAxisMapping" "4 5"
 EndSection
 
 # ************************************************** ********************
 # Monitor section
 # ************************************************** ********************
 
 Section "Monitor"
 Identifier "monitor1"
 VendorName "Generic"
 ModelName "Flat Panel 1280x800"
 HorizSync 28-64
 VertRefresh 43-60
 Option "DPMS"
 
 # HorizSync 31.5-90
 # VertRefresh 60
 
 #Modeline "1280x800 at 70" 101.92 1280 1312 1696 1728 800 816 825 841
 Modeline "1280x800 at 60" 83.91 1280 1312 1624 1656 800 816 824 841
# Modeline "1024x768"    85    1280 1296 1512 1568   854  864  876  908
 
 
 # Sony Vaio C1(X,XS,VE,VN)?
 # 1024x480 @ 85.6 Hz, 48 kHz hsync
 #ModeLine "1024x480" 65.00 1024 1032 1176 1344 480 488 494 563
 -hsync -vsync
 
 # Dell D800 and few Inspiron (16/10) 1280x800
 # default : no (driver refuse to load)
 #ModeLine "1280x800 at 60" 147.89 1280 1376 1512 1744 800 801 804 848
 # samsung : yes !
 #ModeLine "1280x800 at 60" 71.0 1280 1328 1360 1440 800 802 808 823
 # 60Hz : yes !
 #ModeLine "1280x800 at 60" 83.5 1280 1344 1480 1680 800 801 804 828
 # ?? : yes !
 #ModeLine "1280x800" 85.7 1280 1360 1496 1712 800 801 804 835
 # 70Hz : no (lesser ersolution + scrolling)
 #ModeLine "1280x800" 101.92 1280 1312 1696 1728 800 816 824 841
 
 
 EndSection
 
 # ************************************************** ********************
 # Graphics device section
 # ************************************************** ********************
 
 # Any number of graphics device sections may be present
 
 
 # Device configured by xorgconfig:
 
 Section "Device"
 Identifier "geforce"
 #Driver "vesa"
 Driver "nvidia"
 Option "DPMS"
 Option "IgnoreEDID" "1"
 
 #VideoRam 65536
 # Insert Clocks lines here if appropriate
 EndSection
 
 
 # ************************************************** ********************
 # Screen sections
 # ************************************************** ********************
 
 # Any number of screen sections may be present. Each describes
 # the configuration of a single screen. A single specific screen section
 # may be specified from the X server command line with the "-screen"
 # option.
 Section "Screen"
 Identifier "Screen 1"
 Device "geforce"
 Monitor "monitor1"
 DefaultDepth 24
 
 Subsection "Display"
 Depth 8
 #Modes "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
 Modes "1280x800"
 ViewPort 0 0
 EndSubsection
 Subsection "Display"
 Depth 16
 #Modes "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
 Modes "1280x800"
 ViewPort 0 0
 EndSubsection
 Subsection "Display"
 Depth 24
 #Modes "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
 Modes "1280x800 at 60"
 ViewPort 0 0
 EndSubsection
 EndSection
 
 # ************************************************** ********************
 # ServerLayout sections.
 # ************************************************** ********************
 
 # Any number of ServerLayout sections may be present. Each describes
 # the way multiple screens are organised. A specific ServerLayout
 # section may be specified from the X server command line with the
 # "-layout" option. In the absence of this, the first section is used.
 # When now ServerLayout section is present, the first Screen section
 # is used alone.
 
 Section "ServerLayout"
 
 # The Identifier line must be present
 Identifier "Simple Layout"
 
 # Each Screen line specifies a Screen section name, and optionally
 # the relative position of other screens. The four names after
 # primary screen name are the screens to the top, bottom, left and right
 # of the primary screen. In this example, screen 2 is located to the
 # right of screen 1.
 
 Screen "Screen 1"
 
 InputDevice "Generic Keyboard"
 InputDevice "Alps Touchpad"
 InputDevice "USB Mouse"
 
 EndSection
 
 
 Section "DRI"
 Mode 0666
 EndSection
 

```

---

### Post by gyaresu on 2005-06-12
You should post your xorg.conf

---

### Post by Whitewolfe on 2005-06-12
[QUOTE=gyaresu]You should post your xorg.conf[/QUOTE]

Edited accordingly.

-WW

---

### Post by Tomas_IV on 2006-05-04
I just found this thread when searching solution for different touchpad related problem and I can see the question is quite outdated, but for others who need to disable the touchpad prmanently and use usb mouse only:
It should be quite easy. Make backup of your xorg.conf and then edit the original. Move the 
```
Option		"CorePointer"
```
line from the touchpad related block to the usb mouse related block and the
```
Option "SendCoreEvents" "true"
```
line the opposite way. Thus your usb mice will become the core pointer device and the touchpad will become a secondary pointing device. 
Now comment out all lines of the touchpad block, that is put hash (#) mark ahead of every line of this
```
Section "InputDevice"
  	Driver  	"synaptics"
        ....
        ....
End Section
```
block. Now the keypad should be disabled, but you have to restartt X server by ctrl-alt-backspace or by logging off and in again for the changes to take effect.
Please note that it may not work this way if you want to use a ps/2 mouse because in this case both devices may share the same section of your xorg.conf.

---

### Post by Whitewolfe on 2006-05-19
I appreciate the reply.

However, I don't believe you properly understood what I was really asking.

I already knew how to turn off the TOUCHPAD.  What I am trying to do (and which does not appear to be supported by Ubuntu's Synaptics support) is to disable the "tap-to-click" function of the touchpad.  The problem is that, due to the position of the pad, it is impossible to touch-type without accidentally touching the pad.  This, in some cases, can cause the cursor in the editing area to move to a different location, with chaotic results.  

Under windows, disabling this feature is a simple matter.  Ubuntu's Synaptics driver doesn't appear to allow it.  Perhaps in the next release.  In the meantime, the problem has become so much an issue in my work that I was forced to go back to Windows XP exclusively :(

Thanks again for trying to help!

---

### Post by pospeselr on 2006-06-04
Whitewolfe, I also have this version of laptop and had the exact same issue with it.  The solution was a patched version of the synaptics driver found here ([http://prinsig.se/weekee/index.php/Touchpad_(hw](http://prinsig.se/weekee/index.php/Touchpad_(hw)) ).  I do not know if this is necessary for the latest dapper release as I don't have access to it yet, but this is also required and originally patched for breezy.  Everything else works perfectly out of the box, apart from the sound buttons which can be bound to whatever commands suit you with xkeysw package, and the media card readers.  Wireless is also quite easy with ndiswrapper, and probably much easier now in dapper with networkmanager.

---

### Post by karthik085 on 2006-06-07
1. [http://ubuntuforums.org/showpost.php?p=94137&postcount=1](http://ubuntuforums.org/showpost.php?p=94137&postcount=1)

2. How about propietrary Nvidia driver? Does it work with that?

[QUOTE=Whitewolfe]This is getting ridiculous:

Ok I've got two major issues and I can't work them out.  I've been through the forums and through google in general, including Kinser's howto.  None of this stuff works and I can't figure out why.  Gotta be something simple but I am out of ideas.

Issue 1:  Synaptics Touchpad.

The system recongises the touchpad out of the box, no problem.  What IS a problem is that it does not seem to be possible to TURN OFF the dang tap thing.  I don't use it.  I don't want it.  I am sick of having to manually turn off the touchpad in order to be able to type without having the thing pick up false clicks when my thumb inadvertently touches the freaking pad.  I DID, through repeated studying of the results of Xorg.0.log, finally figure out how to make the system recongize the touchpad AS synaptics.  I've compiled the kernel with the alps patch.  I've edited xorg.conf until I become nauseous every time I see the words "sudo nano xorg.conf".  Nothing will turn off taps.  Maybe it's impossible, I don't know.  All I know is all the "this works fine for me" stuff doesn't.

Issue 2:  NVIDIA-glx

I can, through extensive trial and error, make the nvidia driver work.  X will start ok, I get the Nvidia logo, etc etc etc.  However, games like Neverwinter Nights and Enemy Territory don't work.  I get video but it's all garbled and seems to be "out of sync".  Again, all the "this xorg.conf works fine for me" stuff doesn't.

Anyone willing to help me figure this out, I would be happy to send info on any config files, etc that you like.   

The system is a Compaq Presario R3000 with the 15" wide screen.  I'm running Kubuntu Hoary.  

Tell me what else you want to know and I will be very happy to oblige and very grateful for any assistance.

-WW

Edited 06/11/05 - xorg.conf follows.   Note that comments in xorg.conf may not actually be relevant.  This .conf is bits and pieces of several others assembled through cut and paste.

```
# ************************************************** ********************
 # Refer to the xorg.conf(5) man page for details about the format of
 # this file.
 # ************************************************** ********************
 
 # ************************************************** ********************
 # Module section -- this section is used to specify
 # which dynamically loadable modules to load.
 # ************************************************** ********************
 #
 Section "Module"
 Load "GLcore"
 Load "synaptics"
 Load "bitmap"
 Load "dbe"
 Load "ddc"
 # Load "dri"
 Load "extmod"
 Load "freetype"
 Load "glx"
 Load "int10"
 Load "record"
 Load "speedo"
 Load "type1"
 Load "vbe"
 EndSection
 
 
 # ************************************************** ********************
 # Files section. This allows default font and rgb paths to be set
 # ************************************************** ********************
 
 Section "Files"
 FontPath "unix/:7100" # local font server
 # if the local font server has problems, we can fall back on these
 FontPath "/usr/lib/X11/fonts/misc"
 FontPath "/usr/lib/X11/fonts/cyrillic"
 FontPath "/usr/lib/X11/fonts/100dpi/:unscaled"
 FontPath "/usr/lib/X11/fonts/75dpi/:unscaled"
 FontPath "/usr/lib/X11/fonts/Type1"
 FontPath "/usr/lib/X11/fonts/CID"
 FontPath "/usr/lib/X11/fonts/Speedo"
 FontPath "/usr/lib/X11/fonts/100dpi"
 FontPath "/usr/lib/X11/fonts/75dpi"
 EndSection
 
 # ************************************************** ********************
 # Server flags section.
 # ************************************************** ********************
 
 Section "ServerFlags"
 
 # Uncomment this to cause a core dump at the spot where a signal is
 # received. This may leave the console in an unusable state, but may
 # provide a better stack trace in the core dump to aid in debugging
 
 # Option "NoTrapSignals"
 
 # Uncomment this to disable the <Crtl><Alt><Fn> VT switch sequence
 # (where n is 1 through 12). This allows clients to receive these key
 # events.
 
 # Option "DontVTSwitch"
 
 # Uncomment this to disable the <Crtl><Alt><BS> server abort sequence
 # This allows clients to receive this key event.
 
 # Option "DontZap"
 
 # Uncomment this to disable the <Crtl><Alt><KP_+>/<KP_-> mode switching
 # sequences. This allows clients to receive these key events.
 
 # Option "Dont Zoom"
 
 # Uncomment this to disable tuning with the xvidtune client. With
 # it the client can still run and fetch card and monitor attributes,
 # but it will not be allowed to change them. If it tries it will
 # receive a protocol error.
 
 # Option "DisableVidModeExtension"
 
 # Uncomment this to enable the use of a non-local xvidtune client.
 
 # Option "AllowNonLocalXvidtune"
 
 # Uncomment this to disable dynamically modifying the input device
 # (mouse and keyboard) settings.
 
 # Option "DisableModInDev"
 
 # Uncomment this to enable the use of a non-local client to
 # change the keyboard or mouse settings (currently only xset).
 
 # Option "AllowNonLocalModInDev"
 
 EndSection
 
 # ************************************************** ********************
 # Input devices
 # ************************************************** ********************
 
 # ************************************************** ********************
 # Core keyboard's InputDevice section
 # ************************************************** ********************
 
 Section "InputDevice"
 Identifier "Generic Keyboard"
 Driver "keyboard"
 Option "CoreKeyboard"
 Option "XkbRules" "xfree86"
 Option "XkbModel" "pc101"
 Option "XkbLayout" "en"
 EndSection
 
 
 # ************************************************** ********************
 # Core Pointer's InputDevice section
 # ************************************************** ********************
 
Section "InputDevice"
  	Driver  	"synaptics"
  	Identifier  	"Alps Touchpad"
	Option		"CorePointer"
  	Option		"Device"  		"/dev/input/event1"
  	Option		"Protocol"		"event"
  	Option		"LeftEdge"		"120"
  	Option		"RightEdge"		"960"
  	Option		"TopEdge"		"120"
  	#Option		"BottomEdge"		"650"
	# Prctically disables horizontal scroll (button 6 & 7)
	Option		"BottomEdge"		"800"
  	Option		"FingerLow"		"14"
  	Option		"FingerHigh"		"15"
  	Option		"MaxTapTime"		"0"
  	Option		"MaxTapMove"		"30"
  	Option		"EmulateMidButtonTime"	"75"
  	Option		"VertScrollDelta"	"20"
  	Option		"HorizScrollDelta"	"20"
  	Option		"MinSpeed"		"0.4"
  	Option		"MaxSpeed"		"1.1"
  	Option		"AccelFactor"		"0.015"
  	Option		"EdgeMotionMinSpeed"	"15"
  	Option		"EdgeMotionMaxSpeed"	"15"
  	Option		"UpDownScrolling"	"1"
  	Option		"CircularScrolling"	"0"
  	Option		"CircScrollDelta"	"0.1"
  	Option		"CircScrollTrigger"	"2"
	Option		"SHMConfig"		"on"
EndSection
 
 Section "InputDevice"
 Identifier "USB Mouse"
 Driver "mouse"
 Option "SendCoreEvents" "true"
 Option "Device" "/dev/input/mice"
 Option "Protocol" "ImPS/2"
 Option "Emulate3Buttons" "true"
 Option "ZAxisMapping" "4 5"
 EndSection
 
 # ************************************************** ********************
 # Monitor section
 # ************************************************** ********************
 
 Section "Monitor"
 Identifier "monitor1"
 VendorName "Generic"
 ModelName "Flat Panel 1280x800"
 HorizSync 28-64
 VertRefresh 43-60
 Option "DPMS"
 
 # HorizSync 31.5-90
 # VertRefresh 60
 
 #Modeline "1280x800 at 70" 101.92 1280 1312 1696 1728 800 816 825 841
 Modeline "1280x800 at 60" 83.91 1280 1312 1624 1656 800 816 824 841
# Modeline "1024x768"    85    1280 1296 1512 1568   854  864  876  908
 
 
 # Sony Vaio C1(X,XS,VE,VN)?
 # 1024x480 @ 85.6 Hz, 48 kHz hsync
 #ModeLine "1024x480" 65.00 1024 1032 1176 1344 480 488 494 563
 -hsync -vsync
 
 # Dell D800 and few Inspiron (16/10) 1280x800
 # default : no (driver refuse to load)
 #ModeLine "1280x800 at 60" 147.89 1280 1376 1512 1744 800 801 804 848
 # samsung : yes !
 #ModeLine "1280x800 at 60" 71.0 1280 1328 1360 1440 800 802 808 823
 # 60Hz : yes !
 #ModeLine "1280x800 at 60" 83.5 1280 1344 1480 1680 800 801 804 828
 # ?? : yes !
 #ModeLine "1280x800" 85.7 1280 1360 1496 1712 800 801 804 835
 # 70Hz : no (lesser ersolution + scrolling)
 #ModeLine "1280x800" 101.92 1280 1312 1696 1728 800 816 824 841
 
 
 EndSection
 
 # ************************************************** ********************
 # Graphics device section
 # ************************************************** ********************
 
 # Any number of graphics device sections may be present
 
 
 # Device configured by xorgconfig:
 
 Section "Device"
 Identifier "geforce"
 #Driver "vesa"
 Driver "nvidia"
 Option "DPMS"
 Option "IgnoreEDID" "1"
 
 #VideoRam 65536
 # Insert Clocks lines here if appropriate
 EndSection
 
 
 # ************************************************** ********************
 # Screen sections
 # ************************************************** ********************
 
 # Any number of screen sections may be present. Each describes
 # the configuration of a single screen. A single specific screen section
 # may be specified from the X server command line with the "-screen"
 # option.
 Section "Screen"
 Identifier "Screen 1"
 Device "geforce"
 Monitor "monitor1"
 DefaultDepth 24
 
 Subsection "Display"
 Depth 8
 #Modes "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
 Modes "1280x800"
 ViewPort 0 0
 EndSubsection
 Subsection "Display"
 Depth 16
 #Modes "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
 Modes "1280x800"
 ViewPort 0 0
 EndSubsection
 Subsection "Display"
 Depth 24
 #Modes "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
 Modes "1280x800 at 60"
 ViewPort 0 0
 EndSubsection
 EndSection
 
 # ************************************************** ********************
 # ServerLayout sections.
 # ************************************************** ********************
 
 # Any number of ServerLayout sections may be present. Each describes
 # the way multiple screens are organised. A specific ServerLayout
 # section may be specified from the X server command line with the
 # "-layout" option. In the absence of this, the first section is used.
 # When now ServerLayout section is present, the first Screen section
 # is used alone.
 
 Section "ServerLayout"
 
 # The Identifier line must be present
 Identifier "Simple Layout"
 
 # Each Screen line specifies a Screen section name, and optionally
 # the relative position of other screens. The four names after
 # primary screen name are the screens to the top, bottom, left and right
 # of the primary screen. In this example, screen 2 is located to the
 # right of screen 1.
 
 Screen "Screen 1"
 
 InputDevice "Generic Keyboard"
 InputDevice "Alps Touchpad"
 InputDevice "USB Mouse"
 
 EndSection
 
 
 Section "DRI"
 Mode 0666
 EndSection
 

```[/QUOTE]

---

