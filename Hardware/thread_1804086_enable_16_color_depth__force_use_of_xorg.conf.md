---
title: "enable 16 color depth / force use of xorg.conf"
date: 2011-07-14
forum: Hardware
---

### Post by caffemusse on 2011-07-14
I am using Lubunto 10.10 on my Acer aspire one, and it works like a charm. 
I need to load som old games via wine, but these games require 16 bit color depth.
For this reason I followed a guide ([http://forum.lxde.org/viewtopic.php?f=3&t=1492#p4135](http://forum.lxde.org/viewtopic.php?f=3&t=1492#p4135)) to create an Xorg.conf file, and edited the apropriate section in the file to 16 bit, rather than 24.

Lubunto however does not seem to pay any attention to the Xorg.conf file settings, and continues to set the screen depth to 24 bit.

The newly edited Xorg.conf file sits in /ect/X11 folder - is this correct ?
Should configurations be made elsewhere, since I am using the LXDM gui rather than KDE/Gnome ?

I have even created a root account in order to get permissions to put the  Xorg.conf file in the x11 folder.

---

### Post by iiiears on 2011-07-14
This script was posted in the forums and on the web some time ago i would like to thank the author and original poster. It works really well.```
#!/bin/bash

resolution=$(zenity --title="Gtk-Xephyr" --list --text="Please select a screen resolution." --column="Select" --column="Option" TRUE 1024x768 FALSE 800x600 FALSE 640x480 --radiolist)

return_value=$?
case $return_value in

1)

echo -e '\E[31m'"Canceled"
exit ;;

0)

display=$(zenity --title="Gtk-Xephyr" --scale --text "Pick a Display Number\n[0 is default and used]" --min-value=1 --max-value=100 --value=2 --step 2)

return_value=$?
case $return_value in

1)

echo -e '\E[31m'"Canceled"
exit ;;

0)

Xephyr -ac -screen $resolution -br -reset -terminate 2> /dev/null :$display &

cmd=$(zenity --title="Gtk-Xephyr" --entry --text "Command to run on Xephyr:" --entry-text "icewm-session")

return_value=$?
case $return_value in

1)

echo -e '\E[31m'"Canceled"
exit ;;

0)

DISPLAY=:$display
$cmd &

exit ;;

esac
esac
esac

exit 0
```

Also this from the wine wiki the author is given credit here though i can't load the original page seems to fallen off the web for the moment.

> 256 color mode

The X server can't switch from 24bpp* mode to 8bpp** mode. Nevertheless, Wine (in general) can run software that uses 8bpp graphics by internally converting bitmaps to formats compatible with the current X server mode (e.g. 24bpp). This is also true for 8bpp DirectDraw games such as Starcraft, C&C Red Alert and Total Annihilation. Such games will output a fixme message

fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8

but for practical purposes it can be ignored. Although the general support for such conversion is there, there may be bugs affecting specific software, and performance is often not on par with native Windows installations. Search Bugzilla and the AppDB for known issues with individual applications.

* "24bpp" = 24-bit color = 16 million colors = Truecolor

** "8bpp" = 8-bit color = 256 colors = color index mode

Workarounds

If your application says that it needs 8bpp or 256 colors even though you have millions of colors available, you may be able to get it working with one of the workarounds below. Any of four major methods are suggested to provide 8bpp to applications. These include:

    * Xephyr (preferred)
    * Xnest
    * VNC
    * Xinit 

Stage 1: Creating a new X11 display

The instructions below allow you to create a new X11 display, with 256 colors, and with an xterm running within it. But:

    *

      Wherever :1 is written you may use :n instead, where n is an unused display number. The default display is usually :0.
    *

      If your shell doesn't accept the "DISPLAY=:1 xterm" syntax, you may need to use something like "env DISPLAY=:1 xterm" instead.
    *

      See also bug 7334. 

Xephyr

Once you have installed Xephyr (Ubuntu: package xserver-xephyr, in universe), you should be able to run something like the following:

Xephyr :1 -ac -screen 800x600x8 &
DISPLAY=:1 xterm

This will create a 800x600 display, in a window, with 8-bit color, and display an xterm in it.

Xnest

Once you have installed Xnest (Ubuntu: package xnest, in main), you should be able to run the following:

Xnest :1 -depth 8 &
DISPLAY=:1 xterm

This will create a display in a window, with 8-bit color, and display an xterm in it. Xnest depends on the parent X11 for various things; in some cases Xnest won't work (-depth 8 fails on many systems).

VNC

Once you have installed VNC (Ubuntu: packages vnc4server and xvnc4viewer, in universe), you should be able to run the following:

vnc4server :1 -cc 3 -depth 8 -geometry 640x480 -localhost

Then issue the command:

xvnc4viewer :1

This will create a virtual 8bpp display (in this example, a 640x480 window containing the virtual screen). This is known as PseudoColor mode in the VNC documentation.

Xinit

Of course you can use just plain ol' X, but that will only work if your modern video card still supports palettized 8bpp displays.

cd "~/.wine/drive_c/Program Files/My game/"
xinit /usr/bin/wine "my game.exe" -- :1 -ac -depth 8

Or for something more sophisticated use xterm:

xinit /usr/bin/xterm -- :1 -ac -depth 8

You can switch between several running X servers and consoles by using the Ctrl+Alt+F1 ... Ctrl+Alt+F10 keyboard shortcuts. On Ubuntu, the initial X server is on tty7 (Ctrl+Alt+F7), and the new X server will be on tty9 (Ctrl+Alt+F9).

Note: You may get a "user not authorized to run the X server, aborting" error message (this happens on Debian and Ubuntu). To work around this, either run xinit as root (or with sudo), or change the "allowed_users=console" line in /etc/X11/Xwrapper.config to read "allowed_users=anybody". If you run xinit as root, a root shell will be running in the xterm, so you need to start another xterm as your normal user (switch back to your main X server, and run DISPLAY=:1 xterm in a non-root shell). Remember: Don't run Wine as root!

Stage 2: Using the new display

To run commands in the xterm on the new display, you need to move the mouse cursor over its window (without a window manager, X11 uses focus-follows-mouse). It is a good idea to run the following commands in the new xterm, as the variable $DISPLAY will be set correctly. You can run commands from another terminal, but be sure to prepend "DISPLAY=:1 " to them.

First, you need a window manager.

metacity &

You can of course use another window manager, but note that compositing WMs like compiz may not work. The default background is either an eye-watering mesh pattern or a solid black. You can change it to gray with:

xsetroot -solid gray50

Instead of gray50, you can use any X11 color name or a hex color value rgb:RR/GG/BB. You can start Wine in the new display with:

cd "$HOME/.wine/drive_c/Program Files/<etc>"
wine <program> <etc>

When you're finished, you can close the new display. This will kill all programs that were running in it. If you used Xinit, type exit in the xterm that appeared initially.

256ColorMode (last edited 2011-01-13 12:11:27 by JörgHöhle)

Kind regards.

---

### Post by realzippy on 2011-07-14
Can you post your current

/etc/X11/xorg.conf

and your

/var/log/Xorg.0.log   ?

---

### Post by iiiears on 2011-07-14
Hello,

Like you i wasn't able to use the xorg.conf to reduce color depth.
You can be fairly certain that some bright person has posted a patch,
 I wasn't able to find it. There are however many workarounds similar to my post. I will keep looking, If you find a patch for xorg post it again here in the forums. A virtual machine with direct video card acess would work.
   Starcraft and Diablo devotees and my wife a rabid scrabble player use xinit Etc.
   It works. 

Not an elegant solution but it works.

Kind Regards.

---

### Post by caffemusse on 2011-07-15
Hi iiiears,

Thx for the effort- amazed such a simple operation in windows (gui supported) is this complicated in ubuntu- usually my experience is the other way round.
What does the script below do? Does it need to be run only once, or what?
> This script was posted in the forums and on the web some time ago i would like to thank the author and original poster. It works really well.

realzippy:

I will post later today.
> Can you post your current

/etc/X11/xorg.conf

and your

/var/log/Xorg.0.log ? 

Any of you know if there is a gui tool to alter the disply for LXDM?

---

### Post by caffemusse on 2011-07-22
Finally found time to post the Xorg files and log- sorry for the delay, I hope you will still try to assist!

Hope you can reply- I will also upgrade to 11.04 to see if that will solve it.:o

<xorg.conf:
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
	Load  "glx"
	Load  "record"
	Load  "extmod"
	Load  "dbe"
	Load  "dri2"
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
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
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



<log:

[    13.356] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    13.356] X Protocol Version 11, Revision 0
[    13.356] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    13.356] Current Operating System: Linux fiona-AOA110 2.6.35-30-generic #54-Ubuntu SMP Tue Jun 7 18:40:23 UTC 2011 i686
[    13.356] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-30-generic root=UUID=6acde70a-93cc-48ab-87c9-7baa7e68d7b3 ro quiet splash
[    13.357] Build Date: 09 January 2011  12:14:58PM
[    13.357] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    13.357] Current version of pixman: 0.18.4
[    13.357] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    13.357] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    13.357] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 22 19:49:00 2011
[    13.358] (==) Using config file: "/etc/X11/xorg.conf"
[    13.358] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    13.359] (==) ServerLayout "X.org Configured"
[    13.359] (**) |-->Screen "Screen0" (0)
[    13.359] (**) |   |-->Monitor "Monitor0"
[    13.360] (**) |   |-->Device "Card0"
[    13.360] (**) |-->Input Device "Mouse0"
[    13.378] (**) |-->Input Device "Keyboard0"
[    13.378] (==) Automatically adding devices
[    13.378] (==) Automatically enabling devices
[    13.379] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    13.379] 	Entry deleted from font path.
[    13.379] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    13.379] 	Entry deleted from font path.
[    13.379] (**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    13.380] (**) ModulePath set to "/usr/lib/xorg/modules"
[    13.380] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    13.380] (WW) Disabling Mouse0
[    13.380] (WW) Disabling Keyboard0
[    13.380] (II) Loader magic: 0x81f9b00
[    13.380] (II) Module ABI versions:
[    13.380] 	X.Org ANSI C Emulation: 0.4
[    13.380] 	X.Org Video Driver: 8.0
[    13.380] 	X.Org XInput driver : 11.0
[    13.380] 	X.Org Server Extension : 4.0
[    13.383] (--) PCI:*(0:0:2:0) 8086:27ae:1025:015b rev 3, Mem @ 0x78480000/524288, 0x60000000/268435456, 0x78500000/262144, I/O @ 0x000060c0/8
[    13.383] (--) PCI: (0:0:2:1) 8086:27a6:1025:015b rev 3, Mem @ 0x78400000/524288
[    13.384] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    13.384] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[    13.384] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[    13.384] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    13.384] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[    13.384] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    13.384] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[    13.384] (II) LoadModule: "glx"
[    13.432] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    13.433] (II) Module glx: vendor="X.Org Foundation"
[    13.433] 	compiled for 1.9.0, module version = 1.0.0
[    13.433] 	ABI class: X.Org Server Extension, version 4.0
[    13.433] (==) AIGLX enabled
[    13.433] (II) Loading extension GLX
[    13.433] (II) LoadModule: "record"
[    13.435] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    13.435] (II) Module record: vendor="X.Org Foundation"
[    13.435] 	compiled for 1.9.0, module version = 1.13.0
[    13.435] 	Module class: X.Org Server Extension
[    13.435] 	ABI class: X.Org Server Extension, version 4.0
[    13.435] (II) Loading extension RECORD
[    13.435] (II) LoadModule: "extmod"
[    13.436] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    13.437] (II) Module extmod: vendor="X.Org Foundation"
[    13.437] 	compiled for 1.9.0, module version = 1.0.0
[    13.437] 	Module class: X.Org Server Extension
[    13.437] 	ABI class: X.Org Server Extension, version 4.0
[    13.437] (II) Loading extension MIT-SCREEN-SAVER
[    13.437] (II) Loading extension XFree86-VidModeExtension
[    13.437] (II) Loading extension XFree86-DGA
[    13.437] (II) Loading extension DPMS
[    13.437] (II) Loading extension XVideo
[    13.437] (II) Loading extension XVideo-MotionCompensation
[    13.437] (II) Loading extension X-Resource
[    13.437] (II) LoadModule: "dbe"
[    13.438] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    13.439] (II) Module dbe: vendor="X.Org Foundation"
[    13.439] 	compiled for 1.9.0, module version = 1.0.0
[    13.439] 	Module class: X.Org Server Extension
[    13.439] 	ABI class: X.Org Server Extension, version 4.0
[    13.439] (II) Loading extension DOUBLE-BUFFER
[    13.439] (II) LoadModule: "dri2"
[    13.456] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    13.457] (II) Module dri2: vendor="X.Org Foundation"
[    13.457] 	compiled for 1.9.0, module version = 1.2.0
[    13.457] 	ABI class: X.Org Server Extension, version 4.0
[    13.457] (II) Loading extension DRI2
[    13.457] (II) LoadModule: "dri"
[    13.458] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    13.458] (II) Module dri: vendor="X.Org Foundation"
[    13.458] 	compiled for 1.9.0, module version = 1.0.0
[    13.458] 	ABI class: X.Org Server Extension, version 4.0
[    13.458] (II) Loading extension XFree86-DRI
[    13.458] (II) LoadModule: "intel"
[    13.459] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    13.460] (II) Module intel: vendor="X.Org Foundation"
[    13.460] 	compiled for 1.9.0, module version = 2.12.0
[    13.460] 	Module class: X.Org Video Driver
[    13.460] 	ABI class: X.Org Video Driver, version 8.0
[    13.460] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    13.479] (++) using VT number 7

[    13.533] drmOpenDevice: node name is /dev/dri/card0
[    13.534] drmOpenDevice: open result is 8, (OK)
[    13.534] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    13.534] drmOpenDevice: node name is /dev/dri/card0
[    13.534] drmOpenDevice: open result is 8, (OK)
[    13.534] drmOpenByBusid: drmOpenMinor returns 8
[    13.534] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    13.534] (II) intel(0): Creating default Display subsection in Screen section
	"Screen0" for depth/fbbpp 24/32
[    13.534] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    13.534] (==) intel(0): RGB weight 888
[    13.534] (==) intel(0): Default visual is TrueColor
[    13.535] (II) intel(0): Integrated Graphics Chipset: Intel(R) 945GME
[    13.535] (--) intel(0): Chipset: "945GME"
[    13.535] (==) intel(0): video overlay key set to 0x101fe
[    13.564] (II) intel(0): Output VGA1 using monitor section Monitor0
[    13.564] (II) intel(0): Output LVDS1 has no monitor section
[    13.596] (II) intel(0): EDID for output VGA1
[    13.596] (II) intel(0): EDID for output LVDS1
[    13.596] (II) intel(0): Manufacturer: AUO  Model: 11c2  Serial#: 0
[    13.596] (II) intel(0): Year: 2008  Week: 1
[    13.596] (II) intel(0): EDID Version: 1.3
[    13.596] (II) intel(0): Digital Display Input
[    13.596] (II) intel(0): Max Image Size [cm]: horiz.: 20  vert.: 11
[    13.596] (II) intel(0): Gamma: 2.20
[    13.596] (II) intel(0): No DPMS capabilities specified
[    13.597] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    13.597] (II) intel(0): First detailed timing is preferred mode
[    13.597] (II) intel(0): redX: 0.573 redY: 0.339   greenX: 0.330 greenY: 0.596
[    13.597] (II) intel(0): blueX: 0.142 blueY: 0.103   whiteX: 0.310 whiteY: 0.330
[    13.597] (II) intel(0): Manufacturer's mask: 0
[    13.597] (II) intel(0): Supported detailed timing:
[    13.597] (II) intel(0): clock: 50.4 MHz   Image Size:  195 x 113 mm
[    13.597] (II) intel(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
[    13.597] (II) intel(0): v_active: 600  v_sync: 603  v_sync_end 604 v_blanking: 625 v_border: 0
[    13.597] (II) intel(0): Unknown vendor-specific block f
[    13.597] (II) intel(0):  AUO
[    13.597] (II) intel(0):  B089AW01 V1
[    13.597] (II) intel(0): EDID (in hex):
[    13.597] (II) intel(0): 	00ffffffffffff0006afc21100000000
[    13.597] (II) intel(0): 	0112010380140b780afa569256549824
[    13.597] (II) intel(0): 	1a4f5400000001010101010101010101
[    13.598] (II) intel(0): 	010101010101b0130040415819201888
[    13.598] (II) intel(0): 	3100c371000000180000000f00000000
[    13.598] (II) intel(0): 	00000000000000000020000000fe0041
[    13.598] (II) intel(0): 	554f0a202020202020202020000000fe
[    13.598] (II) intel(0): 	004230383941573031205631200a0058
[    13.599] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    13.599] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    13.599] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    13.599] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    13.599] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    13.599] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    13.599] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    13.599] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    13.599] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    13.599] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    13.599] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    13.599] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    13.599] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    13.599] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    13.599] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    13.599] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    13.600] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    13.600] (II) intel(0): Printing probed modes for output LVDS1
[    13.600] (II) intel(0): Modeline "1024x600"x60.0   50.40  1024 1048 1184 1344  600 603 604 625 -hsync -vsync (37.5 kHz)
[    13.600] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    13.600] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    13.600] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    13.600] (II) intel(0): Output VGA1 disconnected
[    13.600] (II) intel(0): Output LVDS1 connected
[    13.600] (II) intel(0): Using exact sizes for initial modes
[    13.600] (II) intel(0): Output LVDS1 using initial mode 1024x600
[    13.600] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    13.600] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[    13.601] (==) intel(0): DPI set to (96, 96)
[    13.601] (II) Loading sub module "fb"
[    13.601] (II) LoadModule: "fb"
[    13.602] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.602] (II) Module fb: vendor="X.Org Foundation"
[    13.602] 	compiled for 1.9.0, module version = 1.0.0
[    13.603] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    13.603] (==) Depth 24 pixmap format is 32 bpp
[    13.603] (II) intel(0): [DRI2] Setup complete
[    13.603] (II) intel(0): [DRI2]   DRI driver: i915
[    13.603] (**) intel(0): Tiling enabled
[    13.603] (**) intel(0): SwapBuffers wait enabled
[    13.603] (==) intel(0): VideoRam: 262144 KB
[    13.603] (II) intel(0): Allocated new frame buffer 1024x600 stride 4096, tiled
[    13.612] (II) UXA(0): Driver registered support for the following operations:
[    13.612] (II)         solid
[    13.612] (II)         copy
[    13.612] (II)         composite (RENDER acceleration)
[    13.612] (II)         put_image
[    13.612] (II)         get_image
[    13.612] (==) intel(0): Backing store disabled
[    13.612] (==) intel(0): Silken mouse enabled
[    13.612] (II) intel(0): Initializing HW Cursor
[    13.668] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    13.668] (==) intel(0): DPMS enabled
[    13.668] (==) intel(0): Intel XvMC decoder disabled
[    13.669] (II) intel(0): Set up textured video
[    13.669] (II) intel(0): Set up overlay video
[    13.669] (II) intel(0): direct rendering: DRI2 Enabled
[    13.669] (--) RandR disabled
[    13.669] (II) Initializing built-in extension Generic Event Extension
[    13.669] (II) Initializing built-in extension SHAPE
[    13.669] (II) Initializing built-in extension MIT-SHM
[    13.670] (II) Initializing built-in extension XInputExtension
[    13.670] (II) Initializing built-in extension XTEST
[    13.670] (II) Initializing built-in extension BIG-REQUESTS
[    13.670] (II) Initializing built-in extension SYNC
[    13.670] (II) Initializing built-in extension XKEYBOARD
[    13.670] (II) Initializing built-in extension XC-MISC
[    13.670] (II) Initializing built-in extension SECURITY
[    13.670] (II) Initializing built-in extension XINERAMA
[    13.670] (II) Initializing built-in extension XFIXES
[    13.670] (II) Initializing built-in extension RENDER
[    13.670] (II) Initializing built-in extension RANDR
[    13.670] (II) Initializing built-in extension COMPOSITE
[    13.670] (II) Initializing built-in extension DAMAGE
[    13.670] (II) Initializing built-in extension GESTURE
[    13.766] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    13.766] (II) AIGLX: enabled GLX_INTEL_swap_event
[    13.766] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    13.766] (II) AIGLX: enabled GLX_SGI_make_current_read
[    13.766] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    13.767] (II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
[    13.767] (II) GLX: Initialized DRI2 GL provider for screen 0
[    13.773] (II) intel(0): Setting screen physical size to 270 x 158
[    14.064] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    14.137] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    14.137] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.137] (II) LoadModule: "evdev"
[    14.139] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.140] (II) Module evdev: vendor="X.Org Foundation"
[    14.140] 	compiled for 1.9.0, module version = 2.3.2
[    14.140] 	Module class: X.Org XInput Driver
[    14.140] 	ABI class: X.Org XInput driver, version 11.0
[    14.140] (**) Power Button: always reports core events
[    14.140] (**) Power Button: Device: "/dev/input/event3"
[    14.152] (II) Power Button: Found keys
[    14.152] (II) Power Button: Configuring as keyboard
[    14.152] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    14.152] (**) Option "xkb_rules" "evdev"
[    14.152] (**) Option "xkb_model" "pc105"
[    14.152] (**) Option "xkb_layout" "dk"
[    14.164] (II) XKB: reuse xkmfile /var/lib/xkb/server-709407198873F5BF4583E7D562E34285659E3DFF.xkm
[    14.169] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    14.169] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    14.169] (**) Video Bus: always reports core events
[    14.169] (**) Video Bus: Device: "/dev/input/event5"
[    14.181] (II) Video Bus: Found keys
[    14.181] (II) Video Bus: Configuring as keyboard
[    14.181] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    14.181] (**) Option "xkb_rules" "evdev"
[    14.181] (**) Option "xkb_model" "pc105"
[    14.181] (**) Option "xkb_layout" "dk"
[    14.188] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    14.188] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.188] (**) Power Button: always reports core events
[    14.188] (**) Power Button: Device: "/dev/input/event0"
[    14.197] (II) Power Button: Found keys
[    14.197] (II) Power Button: Configuring as keyboard
[    14.197] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    14.197] (**) Option "xkb_rules" "evdev"
[    14.197] (**) Option "xkb_model" "pc105"
[    14.197] (**) Option "xkb_layout" "dk"
[    14.199] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    14.199] (II) No input driver/identifier specified (ignoring)
[    14.200] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    14.200] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    14.201] (**) Sleep Button: always reports core events
[    14.201] (**) Sleep Button: Device: "/dev/input/event2"
[    14.213] (II) Sleep Button: Found keys
[    14.213] (II) Sleep Button: Configuring as keyboard
[    14.213] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    14.213] (**) Option "xkb_rules" "evdev"
[    14.213] (**) Option "xkb_model" "pc105"
[    14.213] (**) Option "xkb_layout" "dk"
[    14.232] (II) config/udev: Adding input device Acer Crystal Eye webcam (/dev/input/event6)
[    14.232] (**) Acer Crystal Eye webcam: Applying InputClass "evdev keyboard catchall"
[    14.232] (**) Acer Crystal Eye webcam: always reports core events
[    14.232] (**) Acer Crystal Eye webcam: Device: "/dev/input/event6"
[    14.237] (II) Acer Crystal Eye webcam: Found keys
[    14.237] (II) Acer Crystal Eye webcam: Configuring as keyboard
[    14.237] (II) XINPUT: Adding extended input device "Acer Crystal Eye webcam" (type: KEYBOARD)
[    14.237] (**) Option "xkb_rules" "evdev"
[    14.237] (**) Option "xkb_model" "pc105"
[    14.237] (**) Option "xkb_layout" "dk"
[    14.244] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    14.245] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    14.245] (**) AT Translated Set 2 keyboard: always reports core events
[    14.245] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    14.257] (II) AT Translated Set 2 keyboard: Found keys
[    14.257] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    14.257] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    14.257] (**) Option "xkb_rules" "evdev"
[    14.257] (**) Option "xkb_model" "pc105"
[    14.257] (**) Option "xkb_layout" "dk"
[    14.259] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    14.259] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    14.259] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    14.259] (II) LoadModule: "synaptics"
[    14.261] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    14.261] (II) Module synaptics: vendor="X.Org Foundation"
[    14.261] 	compiled for 1.9.0, module version = 1.2.2
[    14.261] 	Module class: X.Org XInput Driver
[    14.262] 	ABI class: X.Org XInput driver, version 11.0
[    14.262] (II) Synaptics touchpad driver version 1.2.2
[    14.262] (**) Option "Device" "/dev/input/event7"
[    14.301] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5888
[    14.301] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 5218
[    14.301] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    14.301] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    14.301] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[    14.337] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    14.337] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    14.360] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    14.360] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    14.360] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    14.360] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    14.360] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    14.400] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    14.880] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    14.880] (II) No input driver/identifier specified (ignoring)
[    15.896] (II) intel(0): EDID vendor "AUO", prod id 4546
[    15.897] (II) intel(0): Printing DDC gathered Modelines:
[    15.897] (II) intel(0): Modeline "1024x600"x0.0   50.40  1024 1048 1184 1344  600 603 604 625 -hsync -vsync (37.5 kHz)
[    15.932] (II) intel(0): EDID vendor "AUO", prod id 4546
[    15.932] (II) intel(0): Printing DDC gathered Modelines:
[    15.932] (II) intel(0): Modeline "1024x600"x0.0   50.40  1024 1048 1184 1344  600 603 604 625 -hsync -vsync (37.5 kHz)

---

### Post by realzippy on 2011-07-22
In the xorg.conf you posted I cannot see "16 bit"  ?
Expected something like  "*DefaultDepth 16*"  :


```
Section "Screen"
Identifier "Screen0"
Device "Card0"
Monitor "Monitor0"
[COLOR="Lime"]DefaultDepth 16[/COLOR]
SubSection "Display"
Depth 16
Modes "1600x1200" "800x600" #or whatever you need
EndSubSection
SubSection "Display"
Depth 24
Modes "1600x1200" "800x600" #or whatever you need
EndSubSection
EndSection

```

---

### Post by caffemusse on 2011-07-23
Yes I agree - any idea how I can proceed from here?

---

### Post by jocko on 2011-07-23
> **caffemusse said:**
> Yes I agree - any idea how I can proceed from here?
Proceed like this:
> **realzippy said:**
> 
```
Section "Screen"
Identifier "Screen0"
Device "Card0"
Monitor "Monitor0"
[COLOR=Lime]DefaultDepth 16[/COLOR]
SubSection "Display"
Depth 16
Modes "1600x1200" "800x600" #or whatever you need
EndSubSection
SubSection "Display"
Depth 24
Modes "1600x1200" "800x600" #or whatever you need
EndSubSection
EndSection

```

---

### Post by realzippy on 2011-07-23
> **caffemusse said:**
> Yes I agree - any idea how I can proceed from here?

Sorry,does this mean you **already have tested** a screen section as suggested,and
it did not work?
..or do you not know how to edit xorg.conf ?

---

