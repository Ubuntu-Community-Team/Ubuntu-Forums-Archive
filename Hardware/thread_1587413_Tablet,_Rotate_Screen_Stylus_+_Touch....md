---
title: "Tablet, Rotate Screen Stylus + Touch..."
date: 2010-10-03
forum: Hardware
---

### Post by WG- on 2010-10-03
Hello,

I was under the false impression that I solved my problems with my tablet notebook. 

I have the following problem.

My stylus and my finger (touch) are seen as two different devices. Of course this is not very awkward. But this gives me some problems. I had the following script which I execute when I go into tablet modus.

```
orientation=`xrandr --query | grep LVDS | awk '{print $4}'`

if [ "$orientation" = "(normal" ]; then
	xrandr -o inverted
        xsetwacom set "Serial Wacom Tablet" Rotate HALF
	gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer 50
	gconftool-2 --set /apps/panel/toplevels/bottom_panel_screen0/size --type integer 50
else
	xrandr -o normal
        xsetwacom set "Serial Wacom Tablet" Rotate None
	gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer 25
	gconftool-2 --set /apps/panel/toplevels/bottom_panel_screen0/size --type integer 25
fi
```

Unfortuantely only my stylus is being rotated but not my touch... I also tried adding 
```
xsetwacom set "Serial Wacom Tablet touch" Rotate HALF / CW / CCW
```

But they are all falsely orientated... Does anyone have an idea how I orientate my "touch" the same as my "stylus"?

ps. to be clear the above script works fine for my Stylus... but not for my fingers (touch) they are still falsely orientated.

---

### Post by Favux on 2010-10-03
Hi WG-,

Several methods are at the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1") in "4) Rotation to tablet".

---

### Post by WG- on 2010-10-03
> **Favux said:**
> Hi WG-,

Several methods are at the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1") in "4) Rotation to tablet".

Hey! I just replied on your message in my other topic. I will read your link now. Already thank you very much for your help. Greatly appreciated.

---

### Post by Favux on 2010-10-03
Hi WG-,

When you said touch didn't rotate I made the guess that you had a TX2z and touch was on evdev.  Since you have a Toshiba M750, touch should be on the wacom driver.  So all we need is to look at the output of your:
```
xinput --list
```
to fix up your script.

Sorry.

---

### Post by WG- on 2010-10-03
> **Favux said:**
> Hi WG-,

When you said touch didn't rotate I made the guess that you had a TX2z and touch was on evdev.  Since you have a Toshiba M750, touch should be on the wacom driver.  So all we need is to look at the output of your:
```
xinput --list
```
to fix up your script.

Sorry.

No worries, I'm already happy that someone helps me :)

> wouter@WG-Tablet:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser              	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch               	id=16	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet                     	id=17	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=18	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; CNA7157                                 	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]


ps. as said in the OP, I already tried things such as

xsetwacom set "Serial Wacom Tablet touch" Rotate HALF / CW / CCW

But they all give me a wrong position when I tab with my finger on the touch screen.

---

### Post by Favux on 2010-10-03
OK, well it could be touch isn't being picked up by wacom and is dropping through to evdev after all.  Or the Synaptic touchpad driver is picking it up.  So let's look at:
```
xinput list-props "Serial Wacom Tablet touch"
```
And your script should be:
```
orientation=`xrandr --query | grep LVDS | awk '{print $4}'`

if [ "$orientation" = "(normal" ]; then
    xrandr -o inverted
        xsetwacom set "Serial Wacom Tablet" Rotate HALF
        xsetwacom set "Serial Wacom Tablet eraser" Rotate HALF
        xsetwacom set "Serial Wacom Tablet touch" Rotate HALF
    gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer 50
    gconftool-2 --set /apps/panel/toplevels/bottom_panel_screen0/size --type integer 50
else
    xrandr -o normal
        xsetwacom set "Serial Wacom Tablet" Rotate None
        xsetwacom set "Serial Wacom Tablet eraser" Rotate None
        xsetwacom set "Serial Wacom Tablet touch" Rotate None
    gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer 25
    gconftool-2 --set /apps/panel/toplevels/bottom_panel_screen0/size --type integer 25
fi
```
By the way that's a new xrandr orientation line to me.

---

### Post by WG- on 2010-10-03
> **Favux said:**
> OK, well it could be touch isn't being picked up by wacom and is dropping through to evdev after all.  Or the Synaptic touchpad driver is picking it up.  So let's look at:
```
xinput list-props "Serial Wacom Tablet touch"
```
And your script should be:
```
orientation=`xrandr --query | grep LVDS | awk '{print $4}'`

if [ "$orientation" = "(normal" ]; then
    xrandr -o inverted
        xsetwacom set "Serial Wacom Tablet" Rotate HALF
        xsetwacom set "Serial Wacom Tablet eraser" Rotate HALF
        xsetwacom set "Serial Wacom Tablet touch" Rotate HALF
    gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer 50
    gconftool-2 --set /apps/panel/toplevels/bottom_panel_screen0/size --type integer 50
else
    xrandr -o normal
        xsetwacom set "Serial Wacom Tablet" Rotate None
        xsetwacom set "Serial Wacom Tablet eraser" Rotate None
        xsetwacom set "Serial Wacom Tablet touch" Rotate None
    gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer 25
    gconftool-2 --set /apps/panel/toplevels/bottom_panel_screen0/size --type integer 25
fi
```
By the way that's a new xrandr orientation line to me.

```
wouter@WG-Tablet:~$ xinput list-props "Serial Wacom Tablet touch"
Device 'Serial Wacom Tablet touch':
	Device Enabled (125):	1
	Device Accel Profile (249):	0
	Device Accel Constant Deceleration (250):	1.000000
	Device Accel Adaptive Deceleration (252):	1.000000
	Device Accel Velocity Scaling (253):	10.000000
	Wacom Tablet Area (316):	0, 0, 4096, 4096
	Wacom Rotation (317):	2
	Wacom Serial IDs (319):	147, 0, 3, 0
	Wacom TwinView Resolution (320):	0, 0, 0, 0
	Wacom Display Options (321):	-1, 0, 1
	Wacom Screen Area (322):	0, 0, 1280, 800
	Wacom Proximity Threshold (323):	0
	Wacom Capacity (324):	-1
	Wacom Pressure Threshold (325):	7
	Wacom Sample and Suppress (326):	2, 4
	Wacom Enable Touch (327):	1
	Wacom Hover Click (328):	1
	Wacom Tool Type (329):	"TOUCH" (331)
	Wacom Button Actions (330):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)

```

This is my output for xinput list-props "Serial Wacom Tablet touch"

---

### Post by Favux on 2010-10-03
Well that's interesting.  Touch is on the wacom driver after all.

Hmmm.  You're in Lucid correct?  Do you have the default wacom X driver xf86-input-wacom installed?  It would be "xserver-xorg-input-wacom" in Synaptic Package manager.

---

### Post by WG- on 2010-10-03
> **Favux said:**
> Well that's interesting.  Touch is on the wacom driver after all.

Hmmm.  You're in Lucid correct?  Do you have the default wacom X driver xf86-input-wacom installed?  It would be "xserver-xorg-input-wacom" in Synaptic Package manager.

Yup it's installed! And I'm sorry what do you mean with Lucid?

---

### Post by Favux on 2010-10-03
Lucid is Lucid Lynx or Ubuntu 10.4.

---

### Post by WG- on 2010-10-03
Yes I've ubuntu 10.4

---

### Post by Favux on 2010-10-03
Alright.  We could look at your Xorg.0.log in /var/log to see if it tells us anything.

Probably what you need to try is upgrading the xf86-input-wacom from the default 0.10.5 in Lucid to 0.10.8+.  The default was early in the development.  There have been a lot of bug fixes and additions for xsetwacom and serial tablet pc's.  If you want to go this route try Section 2 at the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

Let me know what you think.

---

### Post by WG- on 2010-10-03
```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux WG-Tablet 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-25-generic root=UUID=c34df9d0-57ce-44ba-8da2-09ba39b1111c ro quiet splash
Build Date: 21 July 2010  12:47:34PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct  3 19:45:16 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:2a42:1179:000b Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xff400000/4194304, 0xe0000000/268435456, I/O @ 0x0000cff8/8
(--) PCI: (0:0:2:1) 8086:2a43:1179:000b Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xc6000000/1048576
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.9.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) GM45
(--) intel(0): Chipset: "GM45"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output LVDS1 has no monitor section
(II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
(II) intel(0): Output DVI1 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (interlace mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   68.93  1280 1301 1333 1408  800 804 808 816 (49.0 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output LVDS1 connected
(II) intel(0): Output DVI1 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS1 using initial mode 1280x800
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Kernel mode setting active, disabling FBC.
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(==) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 338 x 211
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event2)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "intl"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) XKB: reuse xkmfile /var/lib/xkb/server-A7FBDFA18BF6567675489BB56C6CA005DE143B04.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event10)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event10"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "intl"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "intl"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device Lid Switch (/dev/input/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event11)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
(**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event5"
(II) Logitech USB Receiver: Found 20 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Configuring as mouse
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(II) Logitech USB Receiver: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event6)
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event6"
(II) Logitech USB Receiver: Found 1 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found absolute axes
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "intl"
(**) Option "xkb_options" "lv3:ralt_switch"
(EE) Logitech USB Receiver: failed to initialize for relative axes.
(II) Logitech USB Receiver: initialized for absolute axes.
(II) config/udev: Adding input device CNA7157 (/dev/input/event7)
(**) CNA7157: Applying InputClass "evdev keyboard catchall"
(**) CNA7157: always reports core events
(**) CNA7157: Device: "/dev/input/event7"
(II) CNA7157: Found keys
(II) CNA7157: Configuring as keyboard
(II) XINPUT: Adding extended input device "CNA7157" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "intl"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "intl"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device PS/2 Mouse (/dev/input/event8)
(**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event8"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found relative axes
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(II) PS/2 Mouse: initialized for relative axes.
(II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event9)
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev pointer catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event9"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 0
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse3)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS0)
(**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.10.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/ttyS0"
(II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
(II) Serial Wacom Tablet: other types will be automatically added.
(**) Serial Wacom Tablet: always reports core events
(**) Option "Button2" "3"
(II) Serial Wacom Tablet: hotplugging dependent devices.
(**) Option "Device" "/dev/ttyS0"
(**) Serial Wacom Tablet eraser: always reports core events
(**) Option "Button2" "3"
(II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER)
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(II) Serial Wacom Tablet eraser: serial tablet id 0x93.
(--) Serial Wacom Tablet eraser: using pressure threshold of 7 for button 1
(--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet speed=38400 maxX=26112 maxY=16320 maxZ=127 resX=2540 resY=2540  tilt=disabled
(--) Serial Wacom Tablet eraser: top X=0 top Y=0 bottom X=26112 bottom Y=16320 resol X=2540 resol Y=2540
(**) Option "Device" "/dev/ttyS0"
(**) Serial Wacom Tablet touch: always reports core events
(**) Option "Button2" "3"
(II) XINPUT: Adding extended input device "Serial Wacom Tablet touch" (type: TOUCH)
(--) Serial Wacom Tablet touch: top X=0 top Y=0 bottom X=4096 bottom Y=4096 resol X=2540 resol Y=2540
(II) Serial Wacom Tablet: hotplugging completed.
(II) XINPUT: Adding extended input device "Serial Wacom Tablet" (type: STYLUS)
(--) Serial Wacom Tablet: top X=0 top Y=0 bottom X=26112 bottom Y=16320 resol X=2540 resol Y=2540
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) XKB: reuse xkmfile /var/lib/xkb/server-9D6B394AF16034C7F55CB3FBE93A656134651BF4.xkm
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
```

This is what the log says. I will try the other thing in a minut.

---

### Post by Favux on 2010-10-03
The Xorg.0.log seems to indicate the wacom devices are being handled correctly, which is what we thought.  I'm not sure what:
```
mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
. . . . .
```
is about.  But I don't think it would interfere with touch.  Did you add any entries to your xorg.conf.

One other thing you could try is another script with a different xrandr line.  See method 1 in the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  Or try method 3.

---

### Post by WG- on 2010-10-03
Ok thanks for your replies Favux. I need to attend now to some exercies for my university now. I will let you know the resulte tomorrow.

Already thank you very much for your help! If I would be able to give kuddes you would've gotten infinty ;)

---

### Post by WG- on 2010-10-03
> **Favux said:**
> The Xorg.0.log seems to indicate the wacom devices are being handled correctly, which is what we thought.  I'm not sure what:
```
mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
[mi] miSpriteRealizeCursor called for floating device.
[mi] miSpriteSetCursor called for floating device.
. . . . .
```
is about.  But I don't think it would interfere with touch.  Did you add any entries to your xorg.conf.

One other thing you could try is another script with a different xrandr line.  See method 1 in the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  Or try method 3.

ps. where is my xorg.conf located? I googled and it should be in /usr/lib/x11/ but can't find any... only a map called xorg.conf.d

---

### Post by Favux on 2010-10-03
Most configuration is now done in xorg.conf.d.  The xorg.conf would be in /etc/X11 if you had one.  As you see it can be absent in a Lucid install if your video chipset (if you had the Nvidia proprietary drivers you'd have one) doesn't need it.  You can think of the xxxx.conf files in /usr/lib/X11/xorg.conf.d as extensions or sections of the xorg.conf.

---

### Post by WG- on 2010-10-03
Ok thanks for the explanation. I just tried the other xrandr commands but none of them worked. The wacom settings weren't correct. I gonne try now the second link.

---

### Post by WG- on 2010-10-03
I've done section 2... but there isn't any process... My stylus is still working correctly and my touch isn't...

---

### Post by Favux on 2010-10-03
Hmmm.  Does any xsetwacom command do anything to touch?  Let's try turning it off:
```
xsetwacom set "Serial Wacom Tablet touch" touch off
```
I'm assuming touch works.

By the way nice job compiling xf86-input-wacom.

---

### Post by WG- on 2010-10-03
The command worked. The tablet doesn't respond on my fingers anymore but still on my stylus...

Also it wasn't that hard I just followed your text and commands ;)

Funny thing however...


> **WG- said:**
> ```
wouter@WG-Tablet:~$ xinput list-props "Serial Wacom Tablet touch"
Device 'Serial Wacom Tablet touch':
	Device Enabled (125):	1
	Device Accel Profile (249):	0
	Device Accel Constant Deceleration (250):	1.000000
	Device Accel Adaptive Deceleration (252):	1.000000
	Device Accel Velocity Scaling (253):	10.000000
	Wacom Tablet Area (316):	0, 0, 4096, 4096
	Wacom Rotation (317):	2
	Wacom Serial IDs (319):	147, 0, 3, 0
	Wacom TwinView Resolution (320):	0, 0, 0, 0
	Wacom Display Options (321):	-1, 0, 1
	Wacom Screen Area (322):	0, 0, 1280, 800
	Wacom Proximity Threshold (323):	0
	Wacom Capacity (324):	-1
	Wacom Pressure Threshold (325):	7
	Wacom Sample and Suppress (326):	2, 4
	Wacom Enable Touch (327):	1
	Wacom Hover Click (328):	1
	Wacom Tool Type (329):	"TOUCH" (331)
	Wacom Button Actions (330):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)

```

This is my output for xinput list-props "Serial Wacom Tablet touch"

I noticted that when listing the properties now, Wacom Rotation (317): 2 is become Wacom Rotation (317):	0

---

### Post by Favux on 2010-10-03
OK, just change 'off' to 'on' and you'll turn it back on.  So we know xsetwacom works on touch which proves touch is on the wacom driver.

So exactly what happens when you rotate to inverted with touch?

---

### Post by WG- on 2010-10-03
> **Favux said:**
> OK, just change 'off' to 'on' and you'll turn it back on.  So we know xsetwacom works on touch which proves touch is on the wacom driver.

So exactly what happens when you rotate to inverted with touch?

yeah i figured that out ;)

What happens is this:

In normal mode.
- When using the stylus the cursor follows the stylus when I hover above the screen and when touching the screen. Tapping is the same as a mouse click.
- When using my fingers the cursor isn't following my fingers of course when I hover, but when I tap the screen the cursor goes to where I tapped and does a mouse click.

Then when I press my rotate button the rotate.sh (which you also edited) is called. And mirrors the screen in vertical mode.
- The stylus is working the same.
- When I now press with my fingers the screen the cursor moves to that point. Only when I release the screen the cursor moves back to the point which is vertical and horizontal mirrored. Also no mouse click is being done.

For example... 
- I touch the screen in the left upper corner. The cursor moves to the left upper corner. When I release the screen the cursor moves to the right lower corner.
- I touch the screen in the right upper corner. The cursor moves to the right upper corner. When I release the screen the cursor moves to the left lower corner.
- I touch the screen in the left middle side. The cursor moves to the left middle side. When I release the screen the cursor moves to the right middle side.

Note that never a mouse click is being "activated"/done by my finger.

When I do xsetwacom set "Serial Wacom Tablet touch" Rotate none the "mouse click" is working again but the orientation is of course completely wrong.

If it is needed I can make a video for better explanation.

---

### Post by Favux on 2010-10-03
Ahhh!  The rotate command is working!  :)  The pointer arrow is going to the finger, not 180 degrees off.  It's more obvious in portrait where it would be 90 degrees off.

What you are describing is another bug of some sort.  There was a jumping cursor bug when rotated to portrait that I filed on the LWP's bug tracker.  But that got fixed.

So a couple of things to try.

Try rotating to portrait (cw or ccw) and see what happens.

Maybe if we set up a xsetwacom configuration script it would help.  Is your touch single finger touch or multitouch on the 750?

---

### Post by WG- on 2010-10-03
It is single touch...

setting this will get the mouse click working again:
xsetwacom set "Serial Wacom Tablet touch" Rotate none

Whenever 
xsetwacom set "Serial Wacom Tablet touch" Rotate Half
xsetwacom set "Serial Wacom Tablet touch" Rotate CW
xsetwacom set "Serial Wacom Tablet touch" Rotate CCW

is being used the orientation gets wrong after I pressed the screen + no mouse click is done.

---

### Post by Favux on 2010-10-03
Alright, this will take me a couple of minutes.  You'll install it as described in IV. in the Bamboo P&T HOW TO.

---

### Post by WG- on 2010-10-03
> **Favux said:**
> Alright, this will take me a couple of minutes.  You'll install it as described in IV. in the Bamboo P&T HOW TO.


That is this thread right? [http://ubuntuforums.org/showpost.php?p=9496609&postcount=1](http://ubuntuforums.org/showpost.php?p=9496609&postcount=1)

However I will try to install section IV then tomorrow. I really need to go to sleep now ;)

Already thank you very much for your help.

---

### Post by Favux on 2010-10-03
Yep, that's the thread.  Good night.

Here's the .xsetwacom.sh for the M750.  I used both "Device names" and ID #'s so you had an example of both.  ID #'s can change if you're hot plugging usb devices.  I commented out the coordinates since they wouldn't apply to your digitizer.

---

### Post by WG- on 2010-10-04
I just tested it and it works! WOOOOOOOOOOOOOOOO  I'm very happy now :D

Now I'm gonne try [https://help.ubuntu.com/community/X61T#Setup](https://help.ubuntu.com/community/X61T#Setup) Automatic Screen Rotation

:) and everything is completed.

ps. those coordinates are for calibration not? Which you can retrieve by using xorg touchscreen calibration.

---

### Post by Favux on 2010-10-04
Hi WG-,

Outstanding!  :)


> ps. those coordinates are for calibration not? Which you can retrieve by using xorg touchscreen calibration. 
Correct.  I left them in as an example or pattern you can follow.  We already know what the wacom driver thinks your coordinates are from the Xorg.0.log when it initialized your tablet:
```
(--) Serial Wacom Tablet: top X=0 top Y=0 bottom X=26112 bottom Y=16320 resol X=2540 resol Y=2540

(--) Serial Wacom Tablet eraser: top X=0 top Y=0 bottom X=26112 bottom Y=16320 resol X=2540 resol Y=2540

(--) Serial Wacom Tablet touch: top X=0 top Y=0 bottom X=4096 bottom Y=4096 resol X=2540 resol Y=2540
```
Notice the stylus and eraser are the same, like you would expect.  And you are right, you can either manually fine tune them or try [xinput_calibrator]("http://www.freedesktop.org/wiki/Software/xinput_calibrator").  Hopefully the ppa or Ubuntu 10.4 links will work for you.

---

### Post by WG- on 2010-10-10
Favux... I think I maybe have a problem with the script you gave me or something else...

Because sometimes (not always) when I've used tablet mode and I execute the rotate.sh script to get back to normal mode the mouse is kind of stuck... it doesn't react then anymore on the left mouse click only on the right... 

```
orientation=`xrandr --query | grep LVDS | awk '{print $4}'`

if [ "$orientation" = "(normal" ]; then
	xrandr -o inverted
		xsetwacom set "Serial Wacom Tablet" Rotate HALF
		xsetwacom set "Serial Wacom Tablet eraser" Rotate HALF
		xsetwacom set "Serial Wacom Tablet touch" Rotate HALF
    gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer 50
    gconftool-2 --set /apps/panel/toplevels/bottom_panel_screen0/size --type integer 50
else
	xrandr -o normal
		xsetwacom set "Serial Wacom Tablet" Rotate None
		xsetwacom set "Serial Wacom Tablet eraser" Rotate None
		xsetwacom set "Serial Wacom Tablet touch" Rotate None
	gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer 25
	gconftool-2 --set /apps/panel/toplevels/bottom_panel_screen0/size --type integer 25
fi
```

This is my rotate.sh script... The following is your xsetwacom.sh script

```
## Device names and ID numbers from 'xinput --list'.

## stylus = ID 17 = "Serial Wacom Tablet"
xsetwacom set "Serial Wacom Tablet" Suppress "2"  		# data trimmed, 1-100
xsetwacom set "Serial Wacom Tablet" RawSample "4"  		# default is 4, 1-?
xsetwacom set "Serial Wacom Tablet" ClickForce "6"  		# 1-21
xsetwacom set "Serial Wacom Tablet" PressCurve "5 10 90 95" 	# default is 0,0,100,100
xsetwacom set "Serial Wacom Tablet" TPCButton "on"
xsetwacom set "Serial Wacom Tablet" Mode "Absolute"  		# or Relative
xsetwacom set "Serial Wacom Tablet" Button1 "1"  		# left mouse click
xsetwacom set "Serial Wacom Tablet" Button2 "3"  		# right mouse click
xsetwacom set "Serial Wacom Tablet" Button3 "2"  		# middle mouse click
#xsetwacom set 12 topy "-101"
#xsetwacom set 12 topx "66"
#xsetwacom set 12 bottomy "16630"
#xsetwacom set 12 bottomx "26416"

## eraser = ID 15 = "Serial Wacom Tablet eraser"
xsetwacom set "Serial Wacom Tablet eraser" Suppress "2"  	# data trimmed, 0-100
xsetwacom set "Serial Wacom Tablet eraser" RawSample "4"  	# default is 4
xsetwacom set "Serial Wacom Tablet eraser" ClickForce "6"  	# 1-21
xsetwacom set "Serial Wacom Tablet eraser" PressCurve "0 10 90 100" # default is 0,0,100,100
xsetwacom set "Serial Wacom Tablet eraser" Mode "Absolute"  	# or Relative
xsetwacom set "Serial Wacom Tablet eraser" Button1 "1"
#xsetwacom set 11 topy "-101"
#xsetwacom set 11 topx "66"
#xsetwacom set 11 bottomy "16630"
#xsetwacom set 11 bottomx "26416"

## touch = ID 16 = "Serial Wacom Tablet touch"
xsetwacom set "Serial Wacom Tablet touch" Touch "on" 		# default
xsetwacom set "Serial Wacom Tablet touch" Suppress "2"  	# data trimmed, 0-100
xsetwacom set "Serial Wacom Tablet touch" ClickForce "1"  	# 1-21, default is 1
xsetwacom set "Serial Wacom Tablet touch" TapTime "250"  	# default is 250 ms
xsetwacom set "Serial Wacom Tablet touch" Mode "Absolute"  	# or Relative
xsetwacom set "Serial Wacom Tablet touch" Button1 "1"
#xsetwacom set 13 topy "215"
#xsetwacom set 13 topx "140"
#xsetwacom set 13 bottomy "3969"
#xsetwacom set 13 bottomx "4028"

## Developed with WG-
```

I'm guessing something is not quiet set in one of the both... Since I only experience the problem when I go back from tablet mode to normal mode.

---

### Post by Favux on 2010-10-10
Hi WG-,

Not sure what's going on.  Does this make any difference?:
```
orientation=`xrandr --query | grep LVDS | awk '{print $4}'`

if [ "$orientation" = "(normal" ]; then
    gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer 50
    gconftool-2 --set /apps/panel/toplevels/bottom_panel_screen0/size --type integer 50
    xrandr -o inverted
        xsetwacom set "Serial Wacom Tablet" Rotate HALF
        xsetwacom set "Serial Wacom Tablet eraser" Rotate HALF
        xsetwacom set "Serial Wacom Tablet touch" Rotate HALF
else
    gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer 24
    gconftool-2 --set /apps/panel/toplevels/bottom_panel_screen0/size --type integer 24
    xrandr -o normal
        xsetwacom set "Serial Wacom Tablet" Rotate None
        xsetwacom set "Serial Wacom Tablet eraser" Rotate None
        xsetwacom set "Serial Wacom Tablet touch" Rotate None
fi
```

---

### Post by WG- on 2010-10-10
> **Favux said:**
> Hi WG-,

Not sure what's going on.  Does this make any difference?:
```
orientation=`xrandr --query | grep LVDS | awk '{print $4}'`

if [ "$orientation" = "(normal" ]; then
    gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer 50
    gconftool-2 --set /apps/panel/toplevels/bottom_panel_screen0/size --type integer 50
    xrandr -o inverted
        xsetwacom set "Serial Wacom Tablet" Rotate HALF
        xsetwacom set "Serial Wacom Tablet eraser" Rotate HALF
        xsetwacom set "Serial Wacom Tablet touch" Rotate HALF
else
    gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer 24
    gconftool-2 --set /apps/panel/toplevels/bottom_panel_screen0/size --type integer 24
    xrandr -o normal
        xsetwacom set "Serial Wacom Tablet" Rotate None
        xsetwacom set "Serial Wacom Tablet eraser" Rotate None
        xsetwacom set "Serial Wacom Tablet touch" Rotate None
fi
```

I will let you know what the result it, since as told it doesn't happen always. I will also try to find out if there is anything specific (other then changing into tablet mode) I'm doing when it occurs.

---

### Post by WG- on 2010-10-14
Didn't work btw. Yesterday and today I experienced the same failure.

---

### Post by WG- on 2010-10-21
I believe I figured out the problem. It happens when CellWriter is active...

---

### Post by Favux on 2010-10-21
Does CellWriter give you any errors when you start it from a terminal?

You may want to go to Synaptic Package Manager and tell it to reinstall CellWriter.

---

