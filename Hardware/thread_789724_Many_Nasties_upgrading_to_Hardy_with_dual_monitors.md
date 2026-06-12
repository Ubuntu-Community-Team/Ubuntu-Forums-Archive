---
title: "Many Nasties upgrading to Hardy with dual monitors"
date: 2008-05-10
forum: Hardware
---

### Post by GnuSense on 2008-05-10
I decided to upgrade a working Kubuntu Feisty system to Hardy, figuring it was LTS and I wouldn't have to do any major tinkering for a long time.  The upgrade to Gutsy went well enough, everything seemed to work, but it was a hard slog getting Hardy to play nice with my hardware, two CRT monitors, a TNT PCI video card and onboard Savage video from my Via chipset KM266 motherboard on a 2 port KVM switch with PS/2 mouse & keyboard.

When I rebooted Hardy for the first time the mouse wasn't working.  I went to init 3 and tried dpkg-reconfigure xserver-xorg, but it wouldn't tab-complete, so I figured it must not be available in Hardy.  So I copied my xorg.conf to a backup location and tried starting X, figuring "bullet proof X" would do its magic. I got to what I later recognized as the Gnome X configuration GUI, displayconfig-gtk.  It wouldn't seem to let me configure my second video card and monitor (or at least, wouldn't save my changes), so booted the default video card and monitor, Presto, I had a rodent again.  Hallelujah, I figured it would be easy enough to edit xorg.conf to set up my dual monitors.  Surprise!  No xorg.conf existed.  None of the GUI tools I was able to find worked. displayconfig-gtk acted like it had initially, not allowing me to save settings.  krandrtray/kcontrol wouldn't let me do anything.  I'd hit the Administrative Mode button but when I went over to the Hardware tab I'd see:

[INDENT]Changes on this tab require 'root' access.
Click the "Administrator Mode" button to allow modifications on this tab
i. This configuration cannot be safely tested[/INDENT]

But there was a red outline over the box, I was in Administrative Mode.  Starting the application as root after copying .Xauthority to my /root directory had the same effect.  Broken.  Here is some of the stuff I got on my konsole:

```
praxis@frug:~$ krandrtray
praxis@frug:~$

Pythonize constructor -- pid = 6675
Python interpreter initialized!



Pythonize constructor -- pid = 6675
IOError [Errno 2] No such file or directory: ''  - will create xorg.conf if possible.
failed to parse display number from ':0' - falling back to default (0)
FATAL: Error inserting battery (/lib/modules/2.6.24-16-386/kernel/drivers/acpi/battery.ko): Operation not permitted
mmap /dev/zero: Permission denied
VESA BIOS Extensions not detected.
FATAL: Error inserting battery (/lib/modules/2.6.24-16-386/kernel/drivers/acpi/battery.ko): Operation not permitted
failed to parse display number from ':0' - falling back to default (0)
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  6
  Minor opcode:  0
  Resource id:  0x3200518
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  12
  Minor opcode:  0
  Resource id:  0x3200518
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  12
  Minor opcode:  0
  Resource id:  0x3200518
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  8
  Minor opcode:  0
  Resource id:  0x3200518
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  12
  Minor opcode:  0
  Resource id:  0x3200518
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  12
  Minor opcode:  0
  Resource id:  0x3200518
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  25
  Minor opcode:  0
  Resource id:  0x3200518
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  25
  Minor opcode:  0
  Resource id:  0x3200518
passprompt

kcmshell: Fatal IO error: client killed

Pythonize constructor -- pid = 6729
Python interpreter initialized!
```

There was no "Debian" menu, which is unwelcome and a first, so I couldn't easily look for other GUI tools.  OK, Kubuntu is Ubuntu's unloved younger brother, it doesn't have essential utilities that are in Ubuntu, I logged in the Gnome. 

Every time I started Gnome I got a dialog box:

[INDENT] "Failed to initialize HAL!". [/INDENT]

I don't know if it hurt anything, I did a: **#/etc/init.d/dbus restart** and continued.

There was no menu entry in the normal place, System -> Administration -> Screens and Graphics.  In the Application -> Other menu there were links to a couple of KDE applications, the krandr stuff and something that summerized my working X setup.  I Googled around until I found that the command for the application was "displayconfig-gtk", but it behaved the same under Gnome, and didn't write a xorg.conf. 

In the meantime I came across lot's of broken stuff, K3B doesn't recognize my CD-RW (Brasero appears to, though I didn't test it), konsole behaves very poorly and is essentially useless in Gnome with my default Transparent, Dark Background schema, the Hardware Testing applet is broken, really, a lot more stuff than I would have expected on a LTS version. 

 When I was in Gnome I noticed a restricted driver manager widgit, so I figured I would try the proprietary nvidia-legacy driver and see if that helped.  I restarted X and got a screen with a single white line, as I recall.  Ctrl+Alt+Backspace didn't restart X.  Attempting to get to another terminal with Ctrl+Alt+F1-6 didn't work either, I had to hit the reset button.  I figured that maybe the restricted manager GUI wasn't kidding when it said I had to restart the computer (instead of just restarting X), but same thing after restarting, no X, no way to get a terminal, hard reset.  I restarted in rescue mode & tried changing NVIDIA to NV in my xorg.conf, but it still froze up when I tried to start X.  What a joy.  I had to uninstall nvidia-legacy from the rescue mode command line to get back in to the GUI, not good.  

Just on a fluke I tried "dpkg-reconfigure xserver-xorg" again, but this time typed the whole thing instead of trying Tab completion.  It still exists!  It basically configured my keyboard and didn't ask me anything else.  I restarted X and had my mouse but still only 1 monitor and no way to configure the second one with the GUI.  But I DID have a xorg.conf!  Victory over communism!  It was extremely rudimentary, but gave me some basic verbiage:

```
# xorg.conf (X.Org X Window System server configuration file)
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

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection
```

Great, so I took my old xorg.conf and basically grafted in the Input Device-Mouse section from the new minimalist xorg.conf on to my old xorg.conf and restarted X and I had dual monitors and a working mouse, but what a largish PITA.  Maybe my experience will be helpful to someone.

My old xorg.conf:

```
Section "ServerLayout"
Identifier     "Xinerama"
Screen      0  "Screen0" 0 0
Screen      1  "Screen1" RightOf "Screen0"
InputDevice    "Mouse0" "CorePointer"
# InputDevice    "Mouse1" "CorePointer"
# InputDevice    "Mouse2" # "CorePointer" # EJB: CorePointer added this one
# InputDevice    "Mouse3" 
# InputDevice    "Mouse4" 
	Option	    "Xinerama" "on"
	Option	    "Clone" "off"

InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
RgbPath      "/usr/share/X11/rgb"
ModulePath   "/usr/lib/xorg/modules"
FontPath     "/usr/lib/X11/fonts/misc/"
FontPath     "/usr/lib/X11/fonts/TTF/"
FontPath     "/usr/lib/X11/fonts/OTF"
FontPath     "/usr/lib/X11/fonts/Type1/"
FontPath     "/usr/lib/X11/fonts/CID/"
FontPath     "/usr/lib/X11/fonts/100dpi/"
FontPath     "/usr/lib/X11/fonts/75dpi/"
EndSection

Section "Module"
Load  "extmod"
Load  "dbe"
Load  "record"
Load  "glx"
Load  "xtrap"
Load  "dri"
Load  "freetype"
Load  "type1"
Load  "freetype"
EndSection

Section "InputDevice"
Identifier  "Keyboard0"
Driver      "kbd"
Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier  "Mouse0"
Driver      "mouse"
Option      "ZAxisMapping" "4 5"
Option      "Buttons" "3"
Option      "AlwaysCore" "true"
Option      "Protocol" "IMPS/2" 
Option      "Device" "/dev/input/mice"
EndSection

## Original
# Section "InputDevice"
# Identifier  "Mouse0"
# Driver      "mouse"
# Option      "ZAxisMapping" "4 5"
# Option      "Buttons" "3"
# Option      "AlwaysCore" "true"
# Option      "Protocol" "ps/2" 
# Option      "Device" "/dev/psaux"
# EndSection


Section "InputDevice"
Identifier  "Mouse1"
Driver      "mouse"
Option      "ZAxisMapping" "4 5"
Option      "Buttons" "3"
Option      "AlwaysCore" "true"
Option      "Protocol" "explorerps/2"
Option      "Device" "/dev/input/mouse0"
EndSection

Section "InputDevice"
Identifier  "Mouse2"
Driver      "mouse"
Option      "ZAxisMapping" "4 5"
Option      "Buttons" "3"
Option      "AlwaysCore" "true"
Option      "Protocol" "auto"
Option      "Device" "/dev/tts/0"
EndSection

Section "InputDevice"
Identifier  "Mouse3"
Driver      "mouse"
Option      "ZAxisMapping" "4 5"
Option      "Buttons" "3"
Option      "AlwaysCore" "true"
Option      "Protocol" "auto"
Option	    "Device" "/dev/mouse"
Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "InputDevice"
Identifier  "Mouse4"
Driver      "mouse"
Option      "ZAxisMapping" "4 5"
Option      "Buttons" "3"
Option      "AlwaysCore" "true"
Option      "Protocol" "imps/2"
Option      "Device" "/dev/input/mouse0"
EndSection

Section "Monitor"
HorizSync    31.5 - 64.3
VertRefresh  60-75
Option       "DPMS"
Identifier   "Monitor0"
VendorName   "Monitor Vendor"
ModelName    "Monitor Model"
EndSection

Section "Monitor"
HorizSync    31.5 - 64.3
VertRefresh  60-75
Option       "DPMS"
Identifier   "Monitor1"
VendorName   "Monitor Vendor"
ModelName    "Monitor Model"
EndSection

Section "Device"
### Available Driver options are:-
### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
### [arg]: arg optional
#Option     "NoAccel"            	# [<bool>]
#Option     "HWCursor"           	# [<bool>]
#Option     "SWCursor"           	# [<bool>]
#Option     "ShadowFB"           	# [<bool>]
#Option     "Rotate"             	# [<str>]
#Option     "UseBIOS"            	# [<bool>]
Option     "UseBIOS" "No"
#Option     "LCDClock"           	# <freq>
#Option     "ShadowStatus"       	# [<bool>]
#Option     "CrtOnly"            	# [<bool>]
#Option     "TvOn"               	# [<bool>]
#Option     "PAL"                	# [<bool>]
#Option     "ForceInit"          	# [<bool>]
#Option     "Overlay"            	# [<str>]
#Option     "TransparencyKey"    	# [<str>]
#Option     "ForceInit"          	# [<bool>]
#Option     "DisableXVMC"        	# [<bool>]
#Option     "DisableTile"        	# [<bool>]
#Option     "DisableCOB"         	# [<bool>]
#Option     "BCIforXv"           	# [<bool>]
#Option     "DVI"                	# [<bool>]
#Option     "BusType"            	# [<str>]
#Option     "DmaType"            	# [<str>]
#Option     "DmaMode"            	# [<str>]
#Option     "AGPMode"            	# <i>
#Option     "AGPSize"            	# <i>
Identifier  "Card0"
Driver      "savage"
VendorName  "S3 Inc."
BoardName   "VT8375 [ProSavage8 KM266/KL266]"
BusID       "PCI:1:0:0"
EndSection

Section "Device"
### Available Driver options are:-
### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
### [arg]: arg optional
#Option     "SWcursor"           	# [<bool>]
#Option     "HWcursor"           	# [<bool>]
#Option     "NoAccel"            	# [<bool>]
#Option     "ShadowFB"           	# [<bool>]
#Option     "UseFBDev"           	# [<bool>]
#Option     "Rotate"             	# [<str>]
#Option     "VideoKey"           	# <i>
#Option     "FlatPanel"          	# [<bool>]
#Option     "FPDither"           	# [<bool>]
#Option     "CrtcNumber"         	# <i>
#Option     "FPScale"            	# [<bool>]
#Option     "FPTweak"            	# <i>
Identifier  "Card1"
Driver      "nv"
VendorName  "nVidia Corporation"
BoardName   "NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
BusID       "PCI:0:8:0"
EndSection



Section "Screen"
Identifier "Screen0"
Device     "Card0"
Monitor    "Monitor0"
DefaultDepth 24
SubSection "Display"
Viewport   0 0
Depth     1
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     4
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     8
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     15
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     16
Modes "1280x1024" "800x600" "640x480"
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     24
Modes "1280x1024" "800x600" "640x480"
EndSubSection
EndSection

Section "Screen"
Identifier "Screen1"
Device     "Card1"
Monitor    "Monitor1"
DefaultDepth 24
SubSection "Display"
Viewport   0 0
Depth     1
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     4
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     8
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     15
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     16
Modes "1280x1024" "800x600" "640x480"
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     24
Modes "1280x1024" "800x600" "640x480"
EndSubSection
EndSection

Section "DRI"
        Group        0
        Mode         0666
EndSection
```

My new xorg.conf:

```
Section "ServerLayout"
Identifier     "Xinerama"
Screen      0  "Screen0" 0 0
Screen      1  "Screen1" RightOf "Screen0"
InputDevice    "Mouse0" "CorePointer"
# InputDevice    "Mouse1" "CorePointer"
# InputDevice    "Mouse2" # "CorePointer" # EJB: CorePointer added this one
# InputDevice    "Mouse3" 
# InputDevice    "Mouse4" 
	Option	    "Xinerama" "on"
	Option	    "Clone" "off"

InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
RgbPath      "/usr/share/X11/rgb"
ModulePath   "/usr/lib/xorg/modules"
FontPath     "/usr/lib/X11/fonts/misc/"
FontPath     "/usr/lib/X11/fonts/TTF/"
FontPath     "/usr/lib/X11/fonts/OTF"
FontPath     "/usr/lib/X11/fonts/Type1/"
FontPath     "/usr/lib/X11/fonts/CID/"
FontPath     "/usr/lib/X11/fonts/100dpi/"
FontPath     "/usr/lib/X11/fonts/75dpi/"
EndSection

Section "Module"
Load  "extmod"
Load  "dbe"
Load  "record"
Load  "glx"
Load  "xtrap"
Load  "dri"
Load  "freetype"
Load  "type1"
Load  "freetype"
EndSection

Section "InputDevice"
Identifier  "Keyboard0"
Driver      "kbd"
Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier  "Mouse0"
Driver      "mouse"
Option      "ZAxisMapping" "4 5"
Option      "Buttons" "3"
Option      "AlwaysCore" "true"
Option      "Protocol" "IMPS/2" 
Option      "Device" "/dev/input/mice"
EndSection

## Original
# Section "InputDevice"
# Identifier  "Mouse0"
# Driver      "mouse"
# Option      "ZAxisMapping" "4 5"
# Option      "Buttons" "3"
# Option      "AlwaysCore" "true"
# Option      "Protocol" "ps/2" 
# Option      "Device" "/dev/psaux"
# EndSection


Section "InputDevice"
Identifier  "Mouse1"
Driver      "mouse"
Option      "ZAxisMapping" "4 5"
Option      "Buttons" "3"
Option      "AlwaysCore" "true"
Option      "Protocol" "explorerps/2"
Option      "Device" "/dev/input/mouse0"
EndSection

Section "InputDevice"
Identifier  "Mouse2"
Driver      "mouse"
Option      "ZAxisMapping" "4 5"
Option      "Buttons" "3"
Option      "AlwaysCore" "true"
Option      "Protocol" "auto"
Option      "Device" "/dev/tts/0"
EndSection

Section "InputDevice"
Identifier  "Mouse3"
Driver      "mouse"
Option      "ZAxisMapping" "4 5"
Option      "Buttons" "3"
Option      "AlwaysCore" "true"
Option      "Protocol" "auto"
Option	    "Device" "/dev/mouse"
Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "InputDevice"
Identifier  "Mouse4"
Driver      "mouse"
Option      "ZAxisMapping" "4 5"
Option      "Buttons" "3"
Option      "AlwaysCore" "true"
Option      "Protocol" "imps/2"
Option      "Device" "/dev/input/mouse0"
EndSection

Section "Monitor"
HorizSync    31.5 - 64.3
VertRefresh  60-75
Option       "DPMS"
Identifier   "Monitor0"
VendorName   "Monitor Vendor"
ModelName    "Monitor Model"
EndSection

Section "Monitor"
HorizSync    31.5 - 64.3
VertRefresh  60-75
Option       "DPMS"
Identifier   "Monitor1"
VendorName   "Monitor Vendor"
ModelName    "Monitor Model"
EndSection

Section "Device"
### Available Driver options are:-
### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
### [arg]: arg optional
#Option     "NoAccel"            	# [<bool>]
#Option     "HWCursor"           	# [<bool>]
#Option     "SWCursor"           	# [<bool>]
#Option     "ShadowFB"           	# [<bool>]
#Option     "Rotate"             	# [<str>]
#Option     "UseBIOS"            	# [<bool>]
Option     "UseBIOS" "No"
#Option     "LCDClock"           	# <freq>
#Option     "ShadowStatus"       	# [<bool>]
#Option     "CrtOnly"            	# [<bool>]
#Option     "TvOn"               	# [<bool>]
#Option     "PAL"                	# [<bool>]
#Option     "ForceInit"          	# [<bool>]
#Option     "Overlay"            	# [<str>]
#Option     "TransparencyKey"    	# [<str>]
#Option     "ForceInit"          	# [<bool>]
#Option     "DisableXVMC"        	# [<bool>]
#Option     "DisableTile"        	# [<bool>]
#Option     "DisableCOB"         	# [<bool>]
#Option     "BCIforXv"           	# [<bool>]
#Option     "DVI"                	# [<bool>]
#Option     "BusType"            	# [<str>]
#Option     "DmaType"            	# [<str>]
#Option     "DmaMode"            	# [<str>]
#Option     "AGPMode"            	# <i>
#Option     "AGPSize"            	# <i>
Identifier  "Card0"
Driver      "savage"
VendorName  "S3 Inc."
BoardName   "VT8375 [ProSavage8 KM266/KL266]"
BusID       "PCI:1:0:0"
EndSection

Section "Device"
### Available Driver options are:-
### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
### [arg]: arg optional
#Option     "SWcursor"           	# [<bool>]
#Option     "HWcursor"           	# [<bool>]
#Option     "NoAccel"            	# [<bool>]
#Option     "ShadowFB"           	# [<bool>]
#Option     "UseFBDev"           	# [<bool>]
#Option     "Rotate"             	# [<str>]
#Option     "VideoKey"           	# <i>
#Option     "FlatPanel"          	# [<bool>]
#Option     "FPDither"           	# [<bool>]
#Option     "CrtcNumber"         	# <i>
#Option     "FPScale"            	# [<bool>]
#Option     "FPTweak"            	# <i>
Identifier  "Card1"
Driver      "nv"
VendorName  "nVidia Corporation"
BoardName   "NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
BusID       "PCI:0:8:0"
EndSection



Section "Screen"
Identifier "Screen0"
Device     "Card0"
Monitor    "Monitor0"
DefaultDepth 24
SubSection "Display"
Viewport   0 0
Depth     1
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     4
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     8
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     15
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     16
Modes "1280x1024" "800x600" "640x480"
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     24
Modes "1280x1024" "800x600" "640x480"
EndSubSection
EndSection

Section "Screen"
Identifier "Screen1"
Device     "Card1"
Monitor    "Monitor1"
DefaultDepth 24
SubSection "Display"
Viewport   0 0
Depth     1
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     4
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     8
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     15
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     16
Modes "1280x1024" "800x600" "640x480"
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     24
Modes "1280x1024" "800x600" "640x480"
EndSubSection
EndSection

Section "DRI"
        Group        0
        Mode         0666
EndSection
```

I really think that maybe Canonical should have held up the release of this version a couple of months (at least) until they hammered out issues like this, xorg 7.3 is a VERY big change and just hasn't had all the bugs worked out yet.

---

