---
title: "monitor configuration help"
date: 2010-10-08
forum: Hardware
---

### Post by shawn.abdushakur on 2010-10-08
Hi,

I have an Optiquest Q191wb monitor attached to an Compaq NX7400 laptop. The laptop no longer has it's own screen so the external monitor is my only display. I'm having trouble getting Ubuntu Lucid to offer the proper resolution for my monitor which is 1280*768 @ 60 Hz. If anyone could dedicate themselves to helping me with this matter, it would be greatly appreciated as this is the computer I let my kids use and I would like it to be as stable and perfect as possible. 

Here is part of my lspci output:

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

Thanks.
Shawn

---

### Post by mikewhatever on 2010-10-08
Can you also post the output of the **xrandr -q** command.
1280x768 resolution is somewhat non-standard. Most recent screens have the aspect ratio of 16:9 (1280x720) or 16:10 (1280x800). Is 1280x768 really the native resolution?

---

### Post by shawn.abdushakur on 2010-10-08
thanks for the help. sorry, the optimal resolution is actually 1440x900 and here's the output:

shawn@NX7400:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 4096 x 4096
VGA1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
LVDS1 connected (normal left inverted right x axis y axis)
   1024x768       60.0 +   85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV1 disconnected (normal left inverted right x axis y axis)

thanks again.

shawn

---

### Post by shawn.abdushakur on 2010-10-08
further to my previous post, if i had an option to switch between 1440x900 and 1280x720, that would be nice. 

thanks again.

shawn

---

### Post by mikewhatever on 2010-10-08
Hm..., the output shows two monitors are connected. Is that the case? If so, which one has the wrong resolution? If not, what's the current resolution of the connected monitor?

I think the way to tackle it would be to generate an xorg.conf (xserver config file) and manually add the desired resolutions.

---

### Post by shawn.abdushakur on 2010-10-08
technically, there are two monitors connected i guess. the original screen on the laptop was damaged so when i removed it, i just cut the wires instead of opening the laptop and disconnecting like i probably should have. the current resolution is 1360x768. 

i'm not sure how to setup an xorg.conf myself.

thanks.

shawn

---

### Post by mikewhatever on 2010-10-08
First close all open windows and safe all unsaved documents. We are going to kill xserver in a moment. You might want to write down the commands, unless there is another computer around.

Hit **ctrl+alt+f1**, this will drop you into a black and white command line environment, login with your username and password.

**sudo -i** #root shell

**service gdm stop** #killing xserver

**cp /etc/X11/xorg.conf /etc/X11/xorg.conf-original** #backing up xorg.conf

**Xorg -configure** #generating the new xorg.conf

**cp /root/xorg.conf.new /etc/X11/xorg.conf** #copying generated file

**exit** #leaving root shell

**sudo service gdm start** #restarting xserver

The last command should get you to the graphical login screen. If everything works as before, the only thing left is to add the resolution you want. To do that, please post the generated xorg.conf:

gksudo gedit /etc/X11/xorg.conf

Here is an example of what it should look like, more or less.
[https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf)

---

### Post by shawn.abdushakur on 2010-10-08
here's my new xorg.conf:


Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "extmod"
	Load  "dbe"
	Load  "glx"
	Load  "dri2"
	Load  "record"
	Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
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
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

thanks.
shawn

---

### Post by mikewhatever on 2010-10-08
OK, cool. Now add the resolutions to the 'Display' subsection at the end of the file.

```
SubSection "Display"
Viewport 0 0
Depth 24
**Mode "1440x900" "1280x720"**
EndSubSection
EndSection
```

Then, logout/login to test.

---

### Post by shawn.abdushakur on 2010-10-08
no dice. here's my new xorg.conf:


Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "extmod"
	Load  "dbe"
	Load  "glx"
	Load  "dri2"
	Load  "record"
	Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Optiquest"
	ModelName    "Q191wb"
	#Modeline
	#Option          "PreferredMode" "1280x1024_60.00"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth	24
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
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes   "1440x900" "1280x720"
	EndSubSection
EndSection

---

### Post by mikewhatever on 2010-10-08
How about this?
```
Section "Monitor"
Identifier "Monitor0"
VendorName "Optiquest"
ModelName "Q191wb"
#Modeline
**Option "PreferredMode" "1440x900_60.00"**
EndSection

```

The '#' sign before a line means the line is commented out, so that the system will ignore it.

If that doesn't help, try adding modlines to the monitor sections. You can generate them with as follows:

```
cvt 1440 900 60
cvt 1280 800 60
```

---

### Post by shawn.abdushakur on 2010-10-08
you got it! i uncommented both lines and added the mode lines for both resolutions. done.

thanks a bunch, man. much appreciated.

shawn

---

### Post by shawn.abdushakur on 2011-11-15
I'm reopening this thread as this solution no longer works since the change to Unity. So, can anyone offer some help in getting this setup for Unity. I'm on Ubuntu 11.10 now which is otherwise very nice. Right now I only have two resolutions available, 1024*768 and 800*600, which, on a 19" monitor, look horrible. Thanks in advance.

Shawn

---

