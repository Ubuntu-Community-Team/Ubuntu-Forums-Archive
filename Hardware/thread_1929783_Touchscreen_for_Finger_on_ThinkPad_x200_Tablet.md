---
title: "Touchscreen for Finger on ThinkPad x200 Tablet"
date: 2012-02-22
forum: Hardware
---

### Post by artmind on 2012-02-22
Hi all

I have problem to calibrate touchscreen for finger. I used xinput_calibrator but it didn't help.
Stylus works perfectly but finger is way off at edges.

Any help would be much appreciated. Thanx

Lenovo x200 Tablet running 11.10 Oneiric Ocelot with latest update

---

### Post by Favux on 2012-02-22
Hi artmind,

Welcome to Ubuntu forums!

Let's see if the Wacom X driver has the touchscreen or if it is on the evdev driver.  Run the following commands in a terminal and post the outputs.
```
xinput list

xsetwacom list
```

---

### Post by artmind on 2012-02-23
xinput list
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                       id=11    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=14    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch                   id=15    [slave  pointer  (2)]

```
xsetwacom list
```
Serial Wacom Tablet stylus          id: 13    type: STYLUS    
Serial Wacom Tablet eraser          id: 14    type: ERASER    
Serial Wacom Tablet touch           id: 15    type: TOUCH  

```thank you for the your help

---

### Post by Favux on 2012-02-23
Well, you are on the Wacom driver so that isn't the problem.

Let's try to see what coordinates X is using for your touchscreen.  What is the output of?
```
xinput list-props "Serial Wacom Tablet touch"
```
Then let's compare it to the coordinates in Xorg.0.log in /var/log.  Compress it by right clicking it and Create Archive and attach it to your next post.

---

### Post by artmind on 2012-02-24
xinput list-props "Serial Wacom Tablet touch"
```

Device 'Serial Wacom Tablet touch':
    Device Enabled (132):    1
    Coordinate Transformation Matrix (134):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (250):    0
    Device Accel Constant Deceleration (251):    1.000000
    Device Accel Adaptive Deceleration (252):    1.000000
    Device Accel Velocity Scaling (253):    10.000000
    Device Node (274):    "/dev/ttyS4"
    Wacom Tablet Area (275):    0, 0, 1024, 1024
    Wacom Rotation (276):    0
    Wacom Pressurecurve (277):    0, 0, 100, 100
    Wacom Serial IDs (278):    147, 0, 3, 0
    Wacom Serial ID binding (279):    0
    Wacom Pressure Threshold (280):    27
    Wacom Sample and Suppress (281):    2, 4
    Wacom Enable Touch (282):    1
    Wacom Enable Touch Gesture (284):    0
    Wacom Touch Gesture Parameters (285):    0, 0, 250
    Wacom Tool Type (286):    "TOUCH" (292)
    Wacom Button Actions (287):    "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
    Device Product ID (288):    1386, 147
    Wacom Debug Levels (289):    0, 0

```

---

### Post by Favux on 2012-02-24
The Xorg.0.log shows the Area the serial digitizer is returning on isdv4GetRanges in wcmISDV4.c (which is in xf86-input-wacom):
```
[    18.962] (--) Serial Wacom Tablet touch: Wacom General ISDV4 tablet maxX=26312 maxY=16520 maxZ=255 resX=100000 resY=100000  tilt=disabled
```
And it is the same for the stylus, eraser, and touch.  Then it steps down the resolution for touch:
```
/* resolution in points/m */
#define ISDV4_PEN_RESOLUTION    100000
#define ISDV4_TOUCH_RESOLUTION  10000
```
and after further processing around line #500 in the code we end up with:
```
    Wacom Tablet Area (275):    0, 0, 1024, 1024
```
Presumably if you did *xinput list-props* on the stylus you'd get the original values unchanged.

I'm wondering why it is square?  The screen isn't square.  It isn't exactly on my USB tablet PC where the numbers are something like:
```
0, 0, 4000, 3875
```
But close.  Is there one direction where the alignment at the screen edges is worse?  Say horizontal or vertical?

What values is xinput_calibrator telling you the touchscreen should have?

---

### Post by artmind on 2012-02-24
Stylus works pefectly!

xinput list-props "Serial Wacom Tablet stylus"

```

Wacom Tablet Area (275):	0, 0, 26312, 16520

```


xinput_calibrator

```

Warning: multiple calibratable devices found, calibrating last one (Serial Wacom Tablet touch)
	use --device to select another one.
Calibrating standard Xorg driver "Serial Wacom Tablet touch"
	current calibration values: min_x=0, max_x=1024 and min_y=0, max_y=1024
	If these values are estimated wrong, either supply it manually with the --precalib option, or run the 'get_precalib.sh' script to automatically get it (through HAL).


--> Making the calibration permanent <--
  copy the snippet below into '/etc/X11/xorg.conf.d/99-calibration.conf'
Section "InputClass"
	Identifier	"calibration"
	MatchProduct	"!!Name_Of_TouchScreen!!"
	Option	"MinX"	"43"
	Option	"MaxX"	"947"
	Option	"MinY"	"86"
	Option	"MaxY"	"943"
EndSection

Change '!!Name_Of_TouchScreen!!' to your device's name in the config above.

```

I tried to set values from xinput_calibrator and values from "xinput list-props "Serial Wacom Tablet stylus"" 
to /etc/X11/xorg.conf.d  and /usr/share/X11/xorg.conf.d/ dirs to 
99-calibration.conf and 50-wacom.conf files, but it didn't help

---

### Post by Favux on 2012-02-25
That helps.  The xinput_calibrator indicate changes from the perfect 1024 x 1024 that list-props is giving you, which are consistent with problems at the screen edges.

Rather than using TopX and Y and Bottom X and Y in .conf files in xorg.conf.d, clear that coordinate stuff out.  Try xsetwacom first to find the values before trying that.  Just type the command in a terminal and enter it and it should instantly apply.  So you can find the right values much more quickly, rather than logging out and in all the time.
```
xsetwacom set "Serial Wacom Tablet touch" Area 43 86 947 943
```
While the x1 and y1 values are suppose to be 0,0 with the default they can be negative numbers if need, i.e. -43 -86.

---

### Post by artmind on 2012-02-25
> Is there one direction where the alignment at the screen edges is worse? Say horizontal or vertical?

No, it's equally from each side.

As I said my stylus works perfectly 

here is the output

xinput list-props "Serial Wacom Tablet stylus"
```

Wacom Tablet Area (275):	0, 0, 26312, 16520

```

 xinput_calibrator
```

Warning: multiple calibratable devices found, calibrating last one (Serial Wacom Tablet touch)
	use --device to select another one.
Calibrating standard Xorg driver "Serial Wacom Tablet touch"
	current calibration values: min_x=0, max_x=1024 and min_y=0, max_y=1024
	If these values are estimated wrong, either supply it manually with the --precalib option, or run the 'get_precalib.sh' script to automatically get it (through HAL).


--> Making the calibration permanent <--
  copy the snippet below into '/etc/X11/xorg.conf.d/99-calibration.conf'
Section "InputClass"
	Identifier	"calibration"
	MatchProduct	"!!Name_Of_TouchScreen!!"
	Option	"MinX"	"39"
	Option	"MaxX"	"948"
	Option	"MinY"	"93"
	Option	"MaxY"	"946"
EndSection

Change '!!Name_Of_TouchScreen!!' to your device's name in the config above.

```"

I tried to set values from xinput_calibrator and values from "xinput list-props "Serial Wacom Tablet stylus"" to 99-calibration.conf and 50-wacom.conf files in /etc/X11/xorg.conf.d/ and /usr/share/X11/xorg.conf.d/ dirs, but it didn't help

PS
sorry.. it's duplicate post

---

### Post by Favux on 2012-02-25
I think you missed my reply in post #8.  Now you have a second set of xinput_calibrator values you can test for touch.

---

### Post by artmind on 2012-02-25
xsetwacom set "Serial Wacom Tablet touch" Area 43 86 947 943

with this command and values it works well!
so how can I set it permanintly?

---

### Post by artmind on 2012-02-25
I add the script to startup. 

Thank you for taking your time to help me!

---

### Post by artmind on 2012-02-25
It's don't work on login screen. 
 
Can you please advice how to set this values correctly?
 
I did everything in accordance with xinput_collibrator output, but it did help.

---

### Post by Favux on 2012-02-25
Good work!  I have to fix touch for my tablet PC also.  While the stylus works fine with the defaults touch doesn't.  So I was wondering if something is going wrong with the touch scaling I talked about earlier.
> It's don't work on login screen. 
The coordinates, either runtime (xsetwacom) or static (xorg.conf.d or xorg.conf) won't apply to the login screen.  That's because X hasn't started yet at the login screen, X starts after you login, and they only apply to X.

I use a startup script like you are now.  By the way there is an example startup script for the X200t attached to the bottom of post #2 on the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  To use a static configuration create a 52-wacom-options.conf in /etc/X11/xorg.conf.d and add:
```
Section "InputClass"
    Identifier "Wacom X200t touch options"
    MatchDriver "wacom"
    MatchProduct "Finger"

    # Apply custom Options to this device below.
    Option "TopX" "43"
    Option "TopY" "86"
    Option "BottomX" "947"
    Option "BottomY" "943"
EndSection
```
This is from:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=USB_Tablets_with_Touch](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=USB_Tablets_with_Touch)
Calibration:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration)
Tablet Configuration:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)
HOWTO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

---

### Post by artmind on 2012-02-25
> The coordinates, either runtime (xsetwacom) or static (xorg.conf.d or xorg.conf) won't apply to the login screen. That's because X hasn't started yet at the login screen, X starts after you login, and they only apply to X.

I think X starts before any GUI start. Stulys and finger works on login screen but the problem with finger is the same, after login everything is perfect. 

Adding line to this file 52-wacom-options.conf doesn't help..

To be honest its not so critical to me and I can live with that. The main problem is solved )

---

### Post by ias on 2012-08-30
Hello,

I have a x200t, but although the stylus works on the screen finger-touching does nothing. Doing the below commands, I don't get the third line at all:

Serial Wacom Tablet touch           id: 15    type: TOUCH  

What can I do ?

Thanks
i

> **artmind said:**
> xinput list
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                       id=11    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=14    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch                   id=15    [slave  pointer  (2)]

```
xsetwacom list
```
Serial Wacom Tablet stylus          id: 13    type: STYLUS    
Serial Wacom Tablet eraser          id: 14    type: ERASER    
Serial Wacom Tablet touch           id: 15    type: TOUCH  

```thank you for the your help

---

### Post by Favux on 2012-08-30
Hi ias,

Silly question but do all X200t's have touch?

You don't say which release of Ubuntu you are running but as I recall there was a bug that affected some serial Wacom tablet PCs a while ago and to get touch turned on they had to run the xsetwacom Touch parameter.  Depending on your device name it would look something like:
```
xsetwacom set "Serial Wacom Tablet touch" Touch on
```
And if you have two finger touch:
```
xsetwacom set "Serial Wacom Tablet touch" Gesture on
```

We could look at your /var/log/Xorg.0.log to find out if it tells us why touch isn't starting.

---

### Post by ias on 2012-08-31
Thanks for answering so quickly. I may have to send this back anyway, so I'd like to try it before I do. 

About touch: if it works in windows, then it should in Ubuntu.. the stylus works already.

Here's what I got:

```
marita@marita-tablet:~$ xsetwacom list
Serial Wacom Tablet stylus      	id: 13	type: STYLUS    
Serial Wacom Tablet eraser      	id: 14	type: ERASER    
marita@marita-tablet:~$ xsetwacom set "Serial Wacom Tablet touch" Touch on
Cannot find device 'Serial Wacom Tablet touch'.
marita@marita-tablet:~$ xsetwacom set "Serial Wacom Tablet Touch" Touch on
Cannot find device 'Serial Wacom Tablet Touch'.

```

I couldn't attach the file you asked for, so here it is

```
[    13.255] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    13.255] X Protocol Version 11, Revision 0
[    13.255] Build Operating System: Linux 2.6.42-26-generic i686 Ubuntu
[    13.255] Current Operating System: Linux marita-tablet 3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686
[    13.255] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=b38af57a-1431-4d87-9331-849d31ae071d ro quiet splash vt.handoff=7
[    13.255] Build Date: 04 August 2012  01:51:24AM
[    13.255] xorg-server 2:1.11.4-0ubuntu10.7 (For technical support please see http://www.ubuntu.com/support) 
[    13.255] Current version of pixman: 0.24.4
[    13.255] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    13.255] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    13.255] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug 31 17:58:00 2012
[    13.273] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    13.273] (==) No Layout section.  Using the first Screen section.
[    13.273] (==) No screen section available. Using defaults.
[    13.273] (**) |-->Screen "Default Screen Section" (0)
[    13.273] (**) |   |-->Monitor "<default monitor>"
[    13.273] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    13.273] (==) Automatically adding devices
[    13.273] (==) Automatically enabling devices
[    13.273] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    13.273] 	Entry deleted from font path.
[    13.273] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    13.273] 	Entry deleted from font path.
[    13.273] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    13.273] 	Entry deleted from font path.
[    13.273] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    13.273] 	Entry deleted from font path.
[    13.273] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    13.273] 	Entry deleted from font path.
[    13.273] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    13.273] 	Entry deleted from font path.
[    13.273] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    13.273] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    13.273] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    13.274] (II) Loader magic: 0xb772e5a0
[    13.274] (II) Module ABI versions:
[    13.274] 	X.Org ANSI C Emulation: 0.4
[    13.274] 	X.Org Video Driver: 11.0
[    13.274] 	X.Org XInput driver : 16.0
[    13.274] 	X.Org Server Extension : 6.0
[    13.275] (--) PCI:*(0:0:2:0) 8086:2a42:17aa:20e4 rev 7, Mem @ 0xf2000000/4194304, 0xd0000000/268435456, I/O @ 0x00001800/8
[    13.275] (--) PCI: (0:0:2:1) 8086:2a43:17aa:20e4 rev 7, Mem @ 0xf2400000/1048576
[    13.275] (II) Open ACPI successful (/var/run/acpid.socket)
[    13.275] (II) LoadModule: "extmod"
[    13.339] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    13.339] (II) Module extmod: vendor="X.Org Foundation"
[    13.339] 	compiled for 1.11.3, module version = 1.0.0
[    13.339] 	Module class: X.Org Server Extension
[    13.339] 	ABI class: X.Org Server Extension, version 6.0
[    13.339] (II) Loading extension MIT-SCREEN-SAVER
[    13.339] (II) Loading extension XFree86-VidModeExtension
[    13.339] (II) Loading extension XFree86-DGA
[    13.339] (II) Loading extension DPMS
[    13.339] (II) Loading extension XVideo
[    13.339] (II) Loading extension XVideo-MotionCompensation
[    13.339] (II) Loading extension X-Resource
[    13.339] (II) LoadModule: "dbe"
[    13.339] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    13.339] (II) Module dbe: vendor="X.Org Foundation"
[    13.339] 	compiled for 1.11.3, module version = 1.0.0
[    13.339] 	Module class: X.Org Server Extension
[    13.339] 	ABI class: X.Org Server Extension, version 6.0
[    13.339] (II) Loading extension DOUBLE-BUFFER
[    13.339] (II) LoadModule: "glx"
[    13.339] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    13.340] (II) Module glx: vendor="X.Org Foundation"
[    13.340] 	compiled for 1.11.3, module version = 1.0.0
[    13.340] 	ABI class: X.Org Server Extension, version 6.0
[    13.340] (==) AIGLX enabled
[    13.340] (II) Loading extension GLX
[    13.340] (II) LoadModule: "record"
[    13.340] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    13.340] (II) Module record: vendor="X.Org Foundation"
[    13.340] 	compiled for 1.11.3, module version = 1.13.0
[    13.340] 	Module class: X.Org Server Extension
[    13.340] 	ABI class: X.Org Server Extension, version 6.0
[    13.340] (II) Loading extension RECORD
[    13.340] (II) LoadModule: "dri"
[    13.340] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    13.340] (II) Module dri: vendor="X.Org Foundation"
[    13.340] 	compiled for 1.11.3, module version = 1.0.0
[    13.340] 	ABI class: X.Org Server Extension, version 6.0
[    13.341] (II) Loading extension XFree86-DRI
[    13.341] (II) LoadModule: "dri2"
[    13.341] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    13.341] (II) Module dri2: vendor="X.Org Foundation"
[    13.341] 	compiled for 1.11.3, module version = 1.2.0
[    13.341] 	ABI class: X.Org Server Extension, version 6.0
[    13.341] (II) Loading extension DRI2
[    13.341] (==) Matched intel as autoconfigured driver 0
[    13.341] (==) Matched vesa as autoconfigured driver 1
[    13.341] (==) Matched fbdev as autoconfigured driver 2
[    13.341] (==) Assigned the driver to the xf86ConfigLayout
[    13.341] (II) LoadModule: "intel"
[    13.341] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    13.341] (II) Module intel: vendor="X.Org Foundation"
[    13.341] 	compiled for 1.11.3, module version = 2.17.0
[    13.341] 	Module class: X.Org Video Driver
[    13.341] 	ABI class: X.Org Video Driver, version 11.0
[    13.341] (II) LoadModule: "vesa"
[    13.342] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    13.342] (II) Module vesa: vendor="X.Org Foundation"
[    13.342] 	compiled for 1.11.3, module version = 2.3.0
[    13.342] 	Module class: X.Org Video Driver
[    13.342] 	ABI class: X.Org Video Driver, version 11.0
[    13.342] (II) LoadModule: "fbdev"
[    13.342] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    13.342] (II) Module fbdev: vendor="X.Org Foundation"
[    13.342] 	compiled for 1.11.3, module version = 0.4.2
[    13.342] 	ABI class: X.Org Video Driver, version 11.0
[    13.342] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    13.342] (II) VESA: driver for VESA chipsets: vesa
[    13.342] (II) FBDEV: driver for framebuffer: fbdev
[    13.342] (++) using VT number 7

[    13.344] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    13.344] (WW) Falling back to old probe method for vesa
[    13.344] (WW) Falling back to old probe method for fbdev
[    13.344] (II) Loading sub module "fbdevhw"
[    13.344] (II) LoadModule: "fbdevhw"
[    13.345] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    13.345] (II) Module fbdevhw: vendor="X.Org Foundation"
[    13.345] 	compiled for 1.11.3, module version = 0.0.2
[    13.345] 	ABI class: X.Org Video Driver, version 11.0
[    13.345] drmOpenDevice: node name is /dev/dri/card0
[    13.345] drmOpenDevice: open result is 9, (OK)
[    13.345] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    13.345] drmOpenDevice: node name is /dev/dri/card0
[    13.345] drmOpenDevice: open result is 9, (OK)
[    13.345] drmOpenByBusid: drmOpenMinor returns 9
[    13.345] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    13.345] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    13.345] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    13.345] (==) intel(0): RGB weight 888
[    13.345] (==) intel(0): Default visual is TrueColor
[    13.345] (II) intel(0): Integrated Graphics Chipset: Intel(R) GM45
[    13.345] (--) intel(0): Chipset: "GM45"
[    13.345] (**) intel(0): Relaxed fencing enabled
[    13.345] (**) intel(0): Wait on SwapBuffers? enabled
[    13.345] (**) intel(0): Triple buffering? enabled
[    13.345] (**) intel(0): Framebuffer tiled
[    13.345] (**) intel(0): Pixmaps tiled
[    13.345] (**) intel(0): 3D buffers tiled
[    13.345] (**) intel(0): SwapBuffers wait enabled
[    13.345] (==) intel(0): video overlay key set to 0x101fe
[    13.345] (II) intel(0): Output LVDS1 has no monitor section
[    13.346] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    13.368] (II) intel(0): Output VGA1 has no monitor section
[    13.455] (II) intel(0): Output HDMI1 has no monitor section
[    13.512] (II) intel(0): Output DP1 has no monitor section
[    13.515] (II) intel(0): Output HDMI2 has no monitor section
[    13.515] (II) intel(0): Output DP2 has no monitor section
[    13.576] (II) intel(0): Output DP3 has no monitor section
[    13.576] (II) intel(0): EDID for output LVDS1
[    13.576] (II) intel(0): Manufacturer: LEN  Model: 4011  Serial#: 0
[    13.576] (II) intel(0): Year: 2008  Week: 0
[    13.576] (II) intel(0): EDID Version: 1.3
[    13.576] (II) intel(0): Digital Display Input
[    13.576] (II) intel(0): Max Image Size [cm]: horiz.: 26  vert.: 16
[    13.576] (II) intel(0): Gamma: 2.20
[    13.576] (II) intel(0): DPMS capabilities: StandBy Suspend Off
[    13.576] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    13.576] (II) intel(0): First detailed timing is preferred mode
[    13.576] (II) intel(0): redX: 0.577 redY: 0.369   greenX: 0.349 greenY: 0.569
[    13.576] (II) intel(0): blueX: 0.150 blueY: 0.122   whiteX: 0.313 whiteY: 0.329
[    13.576] (II) intel(0): Manufacturer's mask: 0
[    13.576] (II) intel(0): Supported detailed timing:
[    13.576] (II) intel(0): clock: 71.1 MHz   Image Size:  261 x 163 mm
[    13.576] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[    13.576] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[    13.576] (II) intel(0): Supported detailed timing:
[    13.576] (II) intel(0): clock: 71.1 MHz   Image Size:  261 x 163 mm
[    13.576] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[    13.576] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[    13.576] (II) intel(0): Unknown vendor-specific block f
[    13.576] (II) intel(0):  HX121WX1-110
[    13.576] (II) intel(0): EDID (in hex):
[    13.576] (II) intel(0): 	00ffffffffffff0030ae114000000000
[    13.576] (II) intel(0): 	00120103801a1078eae795935e599126
[    13.576] (II) intel(0): 	1f505400000001010101010101010101
[    13.576] (II) intel(0): 	010101010101c71b00a0502017303020
[    13.576] (II) intel(0): 	360005a310000019c71b00a050201730
[    13.576] (II) intel(0): 	3020360005a3100000190000000f0081
[    13.576] (II) intel(0): 	0a3c810a3c140a0000009e08000000fe
[    13.576] (II) intel(0): 	0048583132315758312d3131300a0009
[    13.576] (II) intel(0): EDID vendor "LEN", prod id 16401
[    13.576] (II) intel(0): Printing DDC gathered Modelines:
[    13.576] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
[    13.576] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    13.576] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    13.576] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    13.576] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    13.576] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    13.576] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    13.576] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    13.576] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    13.576] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    13.576] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    13.576] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    13.576] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    13.576] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    13.576] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    13.576] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    13.576] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    13.576] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    13.576] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    13.576] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    13.576] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    13.577] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    13.577] (II) intel(0): Printing probed modes for output LVDS1
[    13.577] (II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
[    13.577] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    13.577] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    13.577] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    13.577] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    13.592] (II) intel(0): EDID for output VGA1
[    13.679] (II) intel(0): EDID for output HDMI1
[    13.780] (II) intel(0): EDID for output DP1
[    13.783] (II) intel(0): EDID for output HDMI2
[    13.783] (II) intel(0): EDID for output DP2
[    13.836] (II) intel(0): EDID for output DP3
[    13.836] (II) intel(0): Output LVDS1 connected
[    13.836] (II) intel(0): Output VGA1 disconnected
[    13.836] (II) intel(0): Output HDMI1 disconnected
[    13.836] (II) intel(0): Output DP1 disconnected
[    13.836] (II) intel(0): Output HDMI2 disconnected
[    13.836] (II) intel(0): Output DP2 disconnected
[    13.836] (II) intel(0): Output DP3 disconnected
[    13.836] (II) intel(0): Using exact sizes for initial modes
[    13.836] (II) intel(0): Output LVDS1 using initial mode 1280x800
[    13.836] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    13.836] (II) intel(0): Kernel page flipping support detected, enabling
[    13.836] (**) intel(0): Display dimensions: (260, 160) mm
[    13.836] (**) intel(0): DPI set to (125, 126)
[    13.836] (II) Loading sub module "fb"
[    13.836] (II) LoadModule: "fb"
[    13.836] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.836] (II) Module fb: vendor="X.Org Foundation"
[    13.836] 	compiled for 1.11.3, module version = 1.0.0
[    13.836] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    13.836] (II) Loading sub module "dri2"
[    13.836] (II) LoadModule: "dri2"
[    13.836] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    13.836] (II) Module dri2: vendor="X.Org Foundation"
[    13.836] 	compiled for 1.11.3, module version = 1.2.0
[    13.836] 	ABI class: X.Org Server Extension, version 6.0
[    13.836] (II) UnloadModule: "vesa"
[    13.836] (II) Unloading vesa
[    13.837] (II) UnloadModule: "fbdev"
[    13.837] (II) Unloading fbdev
[    13.837] (II) UnloadModule: "fbdevhw"
[    13.837] (II) Unloading fbdevhw
[    13.837] (==) Depth 24 pixmap format is 32 bpp
[    13.837] (II) intel(0): [DRI2] Setup complete
[    13.837] (II) intel(0): [DRI2]   DRI driver: i965
[    13.837] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[    13.847] (II) UXA(0): Driver registered support for the following operations:
[    13.847] (II)         solid
[    13.847] (II)         copy
[    13.847] (II)         composite (RENDER acceleration)
[    13.847] (II)         put_image
[    13.847] (II)         get_image
[    13.847] (==) intel(0): Backing store disabled
[    13.847] (==) intel(0): Silken mouse enabled
[    13.847] (II) intel(0): Initializing HW Cursor
[    13.876] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    13.878] (==) intel(0): DPMS enabled
[    13.878] (==) intel(0): Intel XvMC decoder enabled
[    13.878] (II) intel(0): Set up textured video
[    13.878] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    13.878] (II) intel(0): direct rendering: DRI2 Enabled
[    13.878] (==) intel(0): hotplug detection: "enabled"
[    13.878] (--) RandR disabled
[    13.878] (II) Initializing built-in extension Generic Event Extension
[    13.878] (II) Initializing built-in extension SHAPE
[    13.878] (II) Initializing built-in extension MIT-SHM
[    13.878] (II) Initializing built-in extension XInputExtension
[    13.878] (II) Initializing built-in extension XTEST
[    13.878] (II) Initializing built-in extension BIG-REQUESTS
[    13.878] (II) Initializing built-in extension SYNC
[    13.878] (II) Initializing built-in extension XKEYBOARD
[    13.878] (II) Initializing built-in extension XC-MISC
[    13.878] (II) Initializing built-in extension SECURITY
[    13.878] (II) Initializing built-in extension XINERAMA
[    13.878] (II) Initializing built-in extension XFIXES
[    13.878] (II) Initializing built-in extension RENDER
[    13.878] (II) Initializing built-in extension RANDR
[    13.878] (II) Initializing built-in extension COMPOSITE
[    13.878] (II) Initializing built-in extension DAMAGE
[    13.896] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    13.896] (II) AIGLX: enabled GLX_INTEL_swap_event
[    13.896] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    13.896] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    13.896] (II) AIGLX: Loaded and initialized i965
[    13.896] (II) GLX: Initialized DRI2 GL provider for screen 0
[    13.897] (II) intel(0): Setting screen physical size to 338 x 211
[    13.906] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.910] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    13.910] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.910] (II) LoadModule: "evdev"
[    13.910] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.910] (II) Module evdev: vendor="X.Org Foundation"
[    13.910] 	compiled for 1.11.3, module version = 2.7.0
[    13.910] 	Module class: X.Org XInput Driver
[    13.910] 	ABI class: X.Org XInput driver, version 16.0
[    13.910] (II) Using input driver 'evdev' for 'Power Button'
[    13.910] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.910] (**) Power Button: always reports core events
[    13.910] (**) evdev: Power Button: Device: "/dev/input/event2"
[    13.910] (--) evdev: Power Button: Vendor 0 Product 0x1
[    13.910] (--) evdev: Power Button: Found keys
[    13.910] (II) evdev: Power Button: Configuring as keyboard
[    13.910] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    13.910] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    13.910] (**) Option "xkb_rules" "evdev"
[    13.910] (**) Option "xkb_model" "pc105"
[    13.910] (**) Option "xkb_layout" "us"
[    13.911] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    13.911] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    13.911] (II) Using input driver 'evdev' for 'Video Bus'
[    13.911] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.911] (**) Video Bus: always reports core events
[    13.911] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    13.911] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    13.911] (--) evdev: Video Bus: Found keys
[    13.911] (II) evdev: Video Bus: Configuring as keyboard
[    13.911] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7/event7"
[    13.911] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    13.911] (**) Option "xkb_rules" "evdev"
[    13.911] (**) Option "xkb_model" "pc105"
[    13.911] (**) Option "xkb_layout" "us"
[    13.912] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    13.912] (II) No input driver specified, ignoring this device.
[    13.912] (II) This device may have been added with another device file.
[    13.912] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    13.912] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    13.912] (II) Using input driver 'evdev' for 'Sleep Button'
[    13.912] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.912] (**) Sleep Button: always reports core events
[    13.912] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    13.912] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    13.912] (--) evdev: Sleep Button: Found keys
[    13.912] (II) evdev: Sleep Button: Configuring as keyboard
[    13.912] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    13.912] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    13.912] (**) Option "xkb_rules" "evdev"
[    13.912] (**) Option "xkb_model" "pc105"
[    13.912] (**) Option "xkb_layout" "us"
[    13.913] (II) config/udev: Adding input device UVC Camera (17ef:480c) (/dev/input/event4)
[    13.913] (**) UVC Camera (17ef:480c): Applying InputClass "evdev keyboard catchall"
[    13.913] (II) Using input driver 'evdev' for 'UVC Camera (17ef:480c)'
[    13.913] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.913] (**) UVC Camera (17ef:480c): always reports core events
[    13.913] (**) evdev: UVC Camera (17ef:480c): Device: "/dev/input/event4"
[    13.913] (--) evdev: UVC Camera (17ef:480c): Vendor 0x17ef Product 0x480c
[    13.913] (--) evdev: UVC Camera (17ef:480c): Found keys
[    13.913] (II) evdev: UVC Camera (17ef:480c): Configuring as keyboard
[    13.913] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input4/event4"
[    13.913] (II) XINPUT: Adding extended input device "UVC Camera (17ef:480c)" (type: KEYBOARD, id 9)
[    13.913] (**) Option "xkb_rules" "evdev"
[    13.913] (**) Option "xkb_model" "pc105"
[    13.913] (**) Option "xkb_layout" "us"
[    13.914] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event10)
[    13.914] (II) No input driver specified, ignoring this device.
[    13.914] (II) This device may have been added with another device file.
[    13.914] (II) config/udev: Adding input device HDA Intel Dock Headphone (/dev/input/event11)
[    13.914] (II) No input driver specified, ignoring this device.
[    13.914] (II) This device may have been added with another device file.
[    13.915] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event8)
[    13.915] (II) No input driver specified, ignoring this device.
[    13.915] (II) This device may have been added with another device file.
[    13.915] (II) config/udev: Adding input device HDA Intel Dock Mic (/dev/input/event9)
[    13.915] (II) No input driver specified, ignoring this device.
[    13.915] (II) This device may have been added with another device file.
[    13.915] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    13.916] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    13.916] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    13.916] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.916] (**) AT Translated Set 2 keyboard: always reports core events
[    13.916] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    13.916] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    13.916] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    13.916] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    13.916] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    13.916] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    13.916] (**) Option "xkb_rules" "evdev"
[    13.916] (**) Option "xkb_model" "pc105"
[    13.916] (**) Option "xkb_layout" "us"
[    13.916] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event6)
[    13.916] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[    13.916] (**) TPPS/2 IBM TrackPoint: Applying InputClass "trackpoint catchall"
[    13.916] (II) Using input driver 'evdev' for 'TPPS/2 IBM TrackPoint'
[    13.916] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.916] (**) TPPS/2 IBM TrackPoint: always reports core events
[    13.916] (**) evdev: TPPS/2 IBM TrackPoint: Device: "/dev/input/event6"
[    13.917] (--) evdev: TPPS/2 IBM TrackPoint: Vendor 0x2 Product 0xa
[    13.917] (--) evdev: TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[    13.917] (--) evdev: TPPS/2 IBM TrackPoint: Found relative axes
[    13.917] (--) evdev: TPPS/2 IBM TrackPoint: Found x and y relative axes
[    13.917] (II) evdev: TPPS/2 IBM TrackPoint: Configuring as mouse
[    13.917] (**) Option "Emulate3Buttons" "true"
[    13.917] (**) Option "EmulateWheel" "true"
[    13.917] (**) Option "EmulateWheelButton" "2"
[    13.917] (**) Option "YAxisMapping" "4 5"
[    13.917] (**) evdev: TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[    13.917] (**) Option "XAxisMapping" "6 7"
[    13.917] (**) evdev: TPPS/2 IBM TrackPoint: XAxisMapping: buttons 6 and 7
[    13.917] (**) evdev: TPPS/2 IBM TrackPoint: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    13.917] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    13.917] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE, id 11)
[    13.917] (II) evdev: TPPS/2 IBM TrackPoint: initialized for relative axes.
[    13.917] (**) TPPS/2 IBM TrackPoint: (accel) keeping acceleration scheme 1
[    13.917] (**) TPPS/2 IBM TrackPoint: (accel) acceleration profile 0
[    13.917] (**) TPPS/2 IBM TrackPoint: (accel) acceleration factor: 2.000
[    13.917] (**) TPPS/2 IBM TrackPoint: (accel) acceleration threshold: 4
[    13.917] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse0)
[    13.917] (II) No input driver specified, ignoring this device.
[    13.917] (II) This device may have been added with another device file.
[    13.920] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event5)
[    13.920] (**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
[    13.920] (II) Using input driver 'evdev' for 'ThinkPad Extra Buttons'
[    13.920] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.920] (**) ThinkPad Extra Buttons: always reports core events
[    13.920] (**) evdev: ThinkPad Extra Buttons: Device: "/dev/input/event5"
[    13.920] (--) evdev: ThinkPad Extra Buttons: Vendor 0x17aa Product 0x5054
[    13.920] (--) evdev: ThinkPad Extra Buttons: Found keys
[    13.920] (II) evdev: ThinkPad Extra Buttons: Configuring as keyboard
[    13.920] (**) Option "config_info" "udev:/sys/devices/platform/thinkpad_acpi/input/input5/event5"
[    13.920] (II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD, id 12)
[    13.920] (**) Option "xkb_rules" "evdev"
[    13.920] (**) Option "xkb_model" "pc105"
[    13.920] (**) Option "xkb_layout" "us"
[    13.920] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS4)
[    13.920] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[    13.920] (II) LoadModule: "wacom"
[    13.921] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    13.921] (II) Module wacom: vendor="X.Org Foundation"
[    13.921] 	compiled for 1.11.3, module version = 0.14.0
[    13.921] 	Module class: X.Org XInput Driver
[    13.921] 	ABI class: X.Org XInput driver, version 16.0
[    13.921] (II) Using input driver 'wacom' for 'Serial Wacom Tablet'
[    13.921] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    13.921] (**) Serial Wacom Tablet: always reports core events
[    13.921] (**) Option "Device" "/dev/ttyS4"
[    13.921] (**) Option "StopBits" "1"
[    13.921] (**) Option "DataBits" "8"
[    13.921] (**) Option "Parity" "None"
[    13.921] (**) Option "Vmin" "1"
[    13.921] (**) Option "Vtime" "10"
[    13.921] (**) Option "FlowControl" "Xoff"
[    13.921] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[    13.921] (II) Serial Wacom Tablet: other types will be automatically added.
[    14.177] (II) Serial Wacom Tablet stylus: serial tablet id 0x90.
[    14.177] (--) Serial Wacom Tablet stylus: using pressure threshold of 27 for button 1
[    14.177] (--) Serial Wacom Tablet stylus: Wacom General ISDV4 tablet maxX=26312 maxY=16520 maxZ=255 resX=100000 resY=100000  tilt=disabled
[    14.177] (II) Serial Wacom Tablet stylus: hotplugging dependent devices.
[    14.177] (EE) Serial Wacom Tablet stylus: Invalid type 'cursor' for this device.
[    14.177] (EE) Serial Wacom Tablet stylus: Invalid type 'touch' for this device.
[    14.177] (EE) Serial Wacom Tablet stylus: Invalid type 'pad' for this device.
[    14.177] (II) Serial Wacom Tablet stylus: hotplugging completed.
[    14.177] (**) Option "config_info" "udev:/sys/devices/pnp0/00:0a/tty/ttyS4"
[    14.177] (II) XINPUT: Adding extended input device "Serial Wacom Tablet stylus" (type: STYLUS, id 13)
[    14.177] (**) Serial Wacom Tablet stylus: (accel) keeping acceleration scheme 1
[    14.177] (**) Serial Wacom Tablet stylus: (accel) acceleration profile 0
[    14.177] (**) Serial Wacom Tablet stylus: (accel) acceleration factor: 2.000
[    14.177] (**) Serial Wacom Tablet stylus: (accel) acceleration threshold: 4
[    14.177] (**) Option "BaudRate" "19200"
[    14.182] (**) Serial Wacom Tablet eraser: Applying InputClass "Wacom serial class"
[    14.182] (II) Using input driver 'wacom' for 'Serial Wacom Tablet eraser'
[    14.182] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    14.182] (**) Serial Wacom Tablet eraser: always reports core events
[    14.182] (**) Option "Device" "/dev/ttyS4"
[    14.182] (**) Option "Type" "eraser"
[    14.182] (**) Option "BaudRate" "19200"
[    14.182] (**) Option "StopBits" "1"
[    14.182] (**) Option "DataBits" "8"
[    14.182] (**) Option "Parity" "None"
[    14.182] (**) Option "Vmin" "1"
[    14.182] (**) Option "Vtime" "10"
[    14.182] (**) Option "FlowControl" "Xoff"
[    14.182] (--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet maxX=26312 maxY=16520 maxZ=255 resX=100000 resY=100000  tilt=disabled
[    14.182] (**) Option "config_info" "udev:/sys/devices/pnp0/00:0a/tty/ttyS4"
[    14.182] (II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER, id 14)
[    14.183] (**) Serial Wacom Tablet eraser: (accel) keeping acceleration scheme 1
[    14.183] (**) Serial Wacom Tablet eraser: (accel) acceleration profile 0
[    14.183] (**) Serial Wacom Tablet eraser: (accel) acceleration factor: 2.000
[    14.183] (**) Serial Wacom Tablet eraser: (accel) acceleration threshold: 4
[    14.866] (II) intel(0): EDID vendor "LEN", prod id 16401
[    14.866] (II) intel(0): Printing DDC gathered Modelines:
[    14.866] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
[    15.880] (II) intel(0): EDID vendor "LEN", prod id 16401
[    15.880] (II) intel(0): Printing DDC gathered Modelines:
[    15.880] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
[    17.608] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[    17.854] (II) intel(0): EDID vendor "LEN", prod id 16401
[    17.854] (II) intel(0): Printing DDC gathered Modelines:
[    17.854] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
[    18.212] (II) intel(0): EDID vendor "LEN", prod id 16401
[    18.212] (II) intel(0): Printing DDC gathered Modelines:
[    18.212] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
[    36.269] (II) intel(0): EDID vendor "LEN", prod id 16401
[    36.269] (II) intel(0): Printing DDC gathered Modelines:
[    36.269] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
```


Thanks for your help!

ias


> **Favux said:**
> Hi ias,

Silly question but do all X200t's have touch?

You don't say which release of Ubuntu you are running but as I recall there was a bug that affected some serial Wacom tablet PCs a while ago and to get touch turned on they had to run the xsetwacom Touch parameter.  Depending on your device name it would look something like:
```
xsetwacom set "Serial Wacom Tablet touch" Touch on
```
And if you have two finger touch:
```
xsetwacom set "Serial Wacom Tablet touch" Gesture on
```

We could look at your /var/log/Xorg.0.log to find out if it tells us why touch isn't starting.

---

### Post by Favux on 2012-08-31
Alright, thanks for not editing the Xorg.0.log.  The Wacom part is:
```
[    13.920] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS4)
[    13.920] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[    13.920] (II) LoadModule: "wacom"
[    13.921] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    13.921] (II) Module wacom: vendor="X.Org Foundation"
[    13.921] 	compiled for 1.11.3, module version = 0.14.0
[    13.921] 	Module class: X.Org XInput Driver
[    13.921] 	ABI class: X.Org XInput driver, version 16.0
[    13.921] (II) Using input driver 'wacom' for 'Serial Wacom Tablet'
[    13.921] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    13.921] (**) Serial Wacom Tablet: always reports core events
[    13.921] (**) Option "Device" "/dev/ttyS4"
[    13.921] (**) Option "StopBits" "1"
[    13.921] (**) Option "DataBits" "8"
[    13.921] (**) Option "Parity" "None"
[    13.921] (**) Option "Vmin" "1"
[    13.921] (**) Option "Vtime" "10"
[    13.921] (**) Option "FlowControl" "Xoff"
[    13.921] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[    13.921] (II) Serial Wacom Tablet: other types will be automatically added.
[    14.177] (II) Serial Wacom Tablet stylus: serial tablet id 0x90.
[    14.177] (--) Serial Wacom Tablet stylus: using pressure threshold of 27 for button 1
[    14.177] (--) Serial Wacom Tablet stylus: Wacom General ISDV4 tablet maxX=26312 maxY=16520 maxZ=255 resX=100000 resY=100000  tilt=disabled
[    14.177] (II) Serial Wacom Tablet stylus: hotplugging dependent devices.
[    14.177] (EE) Serial Wacom Tablet stylus: Invalid type 'cursor' for this device.
[    14.177] (EE) Serial Wacom Tablet stylus: Invalid type 'touch' for this device.
[    14.177] (EE) Serial Wacom Tablet stylus: Invalid type 'pad' for this device.
[    14.177] (II) Serial Wacom Tablet stylus: hotplugging completed.
[    14.177] (**) Option "config_info" "udev:/sys/devices/pnp0/00:0a/tty/ttyS4"
[    14.177] (II) XINPUT: Adding extended input device "Serial Wacom Tablet stylus" (type: STYLUS, id 13)
[    14.177] (**) Serial Wacom Tablet stylus: (accel) keeping acceleration scheme 1
[    14.177] (**) Serial Wacom Tablet stylus: (accel) acceleration profile 0
[    14.177] (**) Serial Wacom Tablet stylus: (accel) acceleration factor: 2.000
[    14.177] (**) Serial Wacom Tablet stylus: (accel) acceleration threshold: 4
[    14.177] (**) Option "BaudRate" "19200"
[    14.182] (**) Serial Wacom Tablet eraser: Applying InputClass "Wacom serial class"
[    14.182] (II) Using input driver 'wacom' for 'Serial Wacom Tablet eraser'
[    14.182] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    14.182] (**) Serial Wacom Tablet eraser: always reports core events
[    14.182] (**) Option "Device" "/dev/ttyS4"
[    14.182] (**) Option "Type" "eraser"
[    14.182] (**) Option "BaudRate" "19200"
[    14.182] (**) Option "StopBits" "1"
[    14.182] (**) Option "DataBits" "8"
[    14.182] (**) Option "Parity" "None"
[    14.182] (**) Option "Vmin" "1"
[    14.182] (**) Option "Vtime" "10"
[    14.182] (**) Option "FlowControl" "Xoff"
[    14.182] (--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet maxX=26312 maxY=16520 maxZ=255 resX=100000 resY=100000  tilt=disabled
[    14.182] (**) Option "config_info" "udev:/sys/devices/pnp0/00:0a/tty/ttyS4"
[    14.182] (II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER, id 14)
[    14.183] (**) Serial Wacom Tablet eraser: (accel) keeping acceleration scheme 1
[    14.183] (**) Serial Wacom Tablet eraser: (accel) acceleration profile 0
[    14.183] (**) Serial Wacom Tablet eraser: (accel) acceleration factor: 2.000
[    14.183] (**) Serial Wacom Tablet eraser: (accel) acceleration threshold: 4
```
And the interesting part is:
```
[    14.177] (II) Serial Wacom Tablet stylus: hotplugging dependent devices.
[    14.177] (EE) Serial Wacom Tablet stylus: Invalid type 'cursor' for this device.
[    14.177] (EE) Serial Wacom Tablet stylus: Invalid type 'touch' for this device.
[    14.177] (EE) Serial Wacom Tablet stylus: Invalid type 'pad' for this device.
[    14.177] (II) Serial Wacom Tablet stylus: hotplugging completed.
```
because it shouldn't be telling us:
```
[    14.177] (EE) Serial Wacom Tablet stylus: Invalid type 'touch' for this device.
```
We know it is not a hardware problem because it works in Windows.  With a serial Wacom tablet PC (the Linux Wacom Project calls it an ISDv4 device) touch is multiplexed with the stylus even though the digitizer and touch screen are two physically separate devices.  This seems to be indicating a bug in the Wacom X driver.

What we could try is updating your xf86-input-wacom driver and see if the bug is already fixed.  That's easy enough.  Did you lose touch after an upgrade to a new release?  What release of Ubuntu are you using?

---

### Post by ias on 2012-08-31
Excellent that you know what you are talking about. I haven't a clue really ;)

If it is a bug in the Wacom X driver, it is odd that I haven't really come across anyone else talking about this problem on the x200t.

It's a second hand machine I got, which I did a clean install of ubuntu 12.04 on (which very annoyingly somehow dovetailed with unrecoverable Blue Screen of Death BSOd behaviour on a clean install of Vista on the other partition!!).

How do I update the driver?

I want to try this out fast, if poss.

Thanks so much.

ias

> 
We know it is not a hardware problem because it works in Windows.  With a serial Wacom tablet PC (the Linux Wacom Project calls it an ISDv4 device) touch is multiplexed with the stylus even though the digitizer and touch screen are two physically separate devices.  This seems to be indicating a bug in the Wacom X driver.

What we could try is updating your xf86-input-wacom driver and see if the bug is already fixed.  That's easy enough.  Did you lose touch after an upgrade to a new release?  What release of Ubuntu are you using?

---

### Post by Favux on 2012-08-31
> If it is a bug in the Wacom X driver, it is odd that I haven't really come across anyone else talking about this problem on the x200t.
Good point, I haven't seen anyone else reporting this in Precise either.  Maybe your install glitched and all that would be needed to solve it is a clean re-install of Precise.

For compiling the xf86-input-wacom driver (the X driver) in Precise you need the build-against-frakenserver.patch.  You can follow the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") and the instructions in [post #1034]("http://ubuntuforums.org/showpost.php?p=12146782&postcount=1034") or follow the instructions in the updated [BambooPT HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110408").  Shouldn't take too long.

---

### Post by ias on 2012-08-31
Thanks. 

I did I fresh install already, and - merde!- same problem. Could it be hardware after all? The wireless switch is loose. Is there any way the touchscreen device could fail without the stylus feature failing? Just asking.. can't check on Windows due to the BSOD.

Will get back to you once I've run through your advice.. but wait - this is quite a huge bunch of code.. mmm.. no easier way???
Is, for example, downloading something from here an option?
[http://sourceforge.net/projects/linuxwacom/files/](http://sourceforge.net/projects/linuxwacom/files/)
What do you do with it then?


> **Favux said:**
> Good point, I haven't seen anyone else reporting this in Precise either.  Maybe your install glitched and all that would be needed to solve it is a clean re-install of Precise.


For compiling the xf86-input-wacom driver (the X driver) in Precise you need the build-against-frakenserver.patch.  You can follow the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") and the instructions in [post #1034]("http://ubuntuforums.org/showpost.php?p=12146782&postcount=1034") or follow the instructions in the updated [BambooPT HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110408").  Shouldn't take too long.

---

### Post by Favux on 2012-08-31
> Is there any way the touchscreen device could fail without the stylus feature failing?
I suppose so if the touchscreen and the digitizer have different cables to the motherboard then the touchscreen's could be loose or broken.  Even if separate I'd guess they're bundled together.  People have fixed loose connections before.  Cable(s) come off the edge of the tablet's screen.  And I think it's a connector it connects to on the screen edge and same on the motherboard.  Or if they have a separate controllers a capacitor or such could be out on the touchscreen.  But I don't know for sure what the hardware is like at that level.

---

