---
title: "Calibrate touch on Lenovo X60"
date: 2012-09-17
forum: Hardware
---

### Post by mmoalem on 2012-09-17
hi there - my laptop is the lenovo x60 tablet with multitouch (both stylus and finger) 
i have installed 12.04 and touch works out of the box. the stylus is fairly precise but i am having difficulty calibrating the finger touch
xinput list returns the following
> &#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch               	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=11	[slave  keyboard (3)]


xinput_calibrator --list doesnt see the touch device...
> 
Device "Serial Wacom Tablet stylus" id=12
Device "Serial Wacom Tablet eraser" id=13


so using xinput-calibrator it retuns only eraser calibration (even though i am using my finger)

> michel@michel-X60-ubuntu:~$ xinput_calibrator
Warning: multiple calibratable devices found, calibrating last one (Serial Wacom Tablet eraser)
	use --device to select another one.
Calibrating standard Xorg driver "Serial Wacom Tablet eraser"
	current calibration values: min_x=0, max_x=24576 and min_y=0, max_y=18432
	If these values are estimated wrong, either supply it manually with the --precalib option, or run the 'get_precalib.sh' script to automatically get it (through HAL).


--> Making the calibration permanent <--
  copy the snippet below into '/etc/X11/xorg.conf.d/99-calibration.conf'
Section "InputClass"
	Identifier	"calibration"
	MatchProduct	"!!Name_Of_TouchScreen!!"
	Option	"MinX"	"10850"
	Option	"MaxX"	"10738"
	Option	"MinY"	"9966"
	Option	"MaxY"	"10110"
	Option	"SwapXY"	"1" # unless it was already set to 1
EndSection

Change '!!Name_Of_TouchScreen!!' to your device's name in the config above.


please help if you can

also need to find how to get auto rotate to work if anyone knows...

---

### Post by Favux on 2012-09-18
Hi mmoalem,

I'm trying to remember if the single finger touch coordinates are the same as the stylus and eraser on a X60t.   Because it is a serial digitizer (ISDv4) and the signals are multiplexed I think they may be.  What is wrong with the touch calibration?

Let's check if the Wacom X driver is seeing touch:
```
xsetwacom list
```

For rotation you could use Magick Rotation:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)  or one of the rotation scripts on the Rotation HOW TO:  [http://ubuntuforums.org/showthread.php?t=996830](http://ubuntuforums.org/showthread.php?t=996830)

---

### Post by mmoalem on 2012-09-18
hi there and thank you very much for trying to help!

this is the output:
> michel@michel-X60-ubuntu:~$ xsetwacom list

Serial Wacom Tablet stylus      	id: 13	type: STYLUS    
Serial Wacom Tablet eraser      	id: 14	type: ERASER    
Serial Wacom Tablet touch       	id: 15	type: TOUCH 
    
michel@michel-X60-ubuntu:~$ xinput list

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Optical USB Mouse              	id=9	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch               	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=12	[slave  keyboard (3)]


michel@michel-X60-ubuntu:~$ xinput_calibrator --list

Device "Serial Wacom Tablet stylus" id=13
Device "Serial Wacom Tablet eraser" id=14

michel@michel-X60-ubuntu:~$ 


touch responds but is not calibrated. 

also touch seems to be relative rather than absolute positioning (stylus is absolute - you put the stylus on the screen and the pointer jumps to the contact point - touch the pointer stays where it is but moves acording to the movment of the touching finger)

---

### Post by Favux on 2012-09-18
Single finger touch for a tablet PC should be Absolute Mode also.  Try:
```
xsetwacom get "Serial Wacom Tablet touch" Mode
```
and see if it returns Absolute.  Either way then run:
```
xsetwacom set "Serial Wacom Tablet touch" Mode Absolute
```
We'll see if that helps.  I'm wondering/guessing if the GNOME Wacom tablet applet in System Settings is messing up your touch and setting it in Relative Mode.

---

### Post by mmoalem on 2012-09-18
hi again - that works but how do i set it to be permanent across boots?
also even in absolute mode it still out of calibration

---

### Post by Favux on 2012-09-18
The driver should be setting it to Absolute by default.  Which is why I'm wondering about the Wacom tablet applet/gnome-settings-daemon.  Might be treating your touch like a Bamboo Pen and Touches touch.  If there is a bug there they may have already fixed it.

With it set to Absolute does xinput_calibrator now pick it up?  Looking at some of the sample serial tablet PC scripts it looks like touch does have different coordinates.  So your touch coordinates should be somewhere around the X200t's and the Toshiba Portege's coordinates.  We can check in Xorg.0.log in /var/log and see if your touch coordinates are there.

You can set up a xsetwacom start up script.  See part IV. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") and the attached example script in post #2 on that thread.

---

### Post by mmoalem on 2012-09-18
thanks again

1. after setting the mode to absolute xinput-calibrator does pick it up

this is the Xorg.0 log

> [     3.901] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[     3.901] X Protocol Version 11, Revision 0
[     3.901] Build Operating System: Linux 2.6.42-26-generic i686 Ubuntu
[     3.901] Current Operating System: Linux michel-X60-ubuntu 3.2.0-30-generic-pae #48-Ubuntu SMP Fri Aug 24 17:14:09 UTC 2012 i686
[     3.901] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-30-generic-pae root=UUID=89796561-d21e-4d12-ab61-f9bd449c3eaa ro quiet splash vt.handoff=7
[     3.901] Build Date: 04 August 2012  01:51:24AM
[     3.901] xorg-server 2:1.11.4-0ubuntu10.7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[     3.901] Current version of pixman: 0.24.4
[     3.901] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[     3.901] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     3.901] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep 18 23:07:07 2012
[     3.902] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     3.904] (==) No Layout section.  Using the first Screen section.
[     3.904] (==) No screen section available. Using defaults.
[     3.904] (**) |-->Screen "Default Screen Section" (0)
[     3.904] (**) |   |-->Monitor "<default monitor>"
[     3.905] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[     3.905] (==) Automatically adding devices
[     3.905] (==) Automatically enabling devices
[     3.906] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     3.906] 	Entry deleted from font path.
[     3.906] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     3.906] 	Entry deleted from font path.
[     3.906] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     3.906] 	Entry deleted from font path.
[     3.906] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     3.906] 	Entry deleted from font path.
[     3.906] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     3.906] 	Entry deleted from font path.
[     3.906] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     3.906] 	Entry deleted from font path.
[     3.906] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[     3.906] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     3.906] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[     3.907] (II) Loader magic: 0xb77635a0
[     3.907] (II) Module ABI versions:
[     3.907] 	X.Org ANSI C Emulation: 0.4
[     3.907] 	X.Org Video Driver: 11.0
[     3.907] 	X.Org XInput driver : 16.0
[     3.907] 	X.Org Server Extension : 6.0
[     3.908] (--) PCI:*(0:0:2:0) 8086:27a2:17aa:201a rev 3, Mem @ 0xee100000/524288, 0xd0000000/268435456, 0xee200000/262144, I/O @ 0x00001800/8
[     3.908] (--) PCI: (0:0:2:1) 8086:27a6:17aa:201a rev 3, Mem @ 0xee180000/524288
[     3.908] (II) Open ACPI successful (/var/run/acpid.socket)
[     3.908] (II) LoadModule: "extmod"
[     3.911] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     3.912] (II) Module extmod: vendor="X.Org Foundation"
[     3.912] 	compiled for 1.11.3, module version = 1.0.0
[     3.912] 	Module class: X.Org Server Extension
[     3.912] 	ABI class: X.Org Server Extension, version 6.0
[     3.912] (II) Loading extension MIT-SCREEN-SAVER
[     3.912] (II) Loading extension XFree86-VidModeExtension
[     3.912] (II) Loading extension XFree86-DGA
[     3.913] (II) Loading extension DPMS
[     3.913] (II) Loading extension XVideo
[     3.913] (II) Loading extension XVideo-MotionCompensation
[     3.913] (II) Loading extension X-Resource
[     3.913] (II) LoadModule: "dbe"
[     3.913] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     3.914] (II) Module dbe: vendor="X.Org Foundation"
[     3.914] 	compiled for 1.11.3, module version = 1.0.0
[     3.914] 	Module class: X.Org Server Extension
[     3.914] 	ABI class: X.Org Server Extension, version 6.0
[     3.914] (II) Loading extension DOUBLE-BUFFER
[     3.914] (II) LoadModule: "glx"
[     3.914] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     3.918] (II) Module glx: vendor="X.Org Foundation"
[     3.918] 	compiled for 1.11.3, module version = 1.0.0
[     3.918] 	ABI class: X.Org Server Extension, version 6.0
[     3.918] (==) AIGLX enabled
[     3.918] (II) Loading extension GLX
[     3.918] (II) LoadModule: "record"
[     3.918] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     3.919] (II) Module record: vendor="X.Org Foundation"
[     3.919] 	compiled for 1.11.3, module version = 1.13.0
[     3.919] 	Module class: X.Org Server Extension
[     3.919] 	ABI class: X.Org Server Extension, version 6.0
[     3.919] (II) Loading extension RECORD
[     3.919] (II) LoadModule: "dri"
[     3.919] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     3.920] (II) Module dri: vendor="X.Org Foundation"
[     3.920] 	compiled for 1.11.3, module version = 1.0.0
[     3.920] 	ABI class: X.Org Server Extension, version 6.0
[     3.920] (II) Loading extension XFree86-DRI
[     3.920] (II) LoadModule: "dri2"
[     3.921] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     3.921] (II) Module dri2: vendor="X.Org Foundation"
[     3.921] 	compiled for 1.11.3, module version = 1.2.0
[     3.921] 	ABI class: X.Org Server Extension, version 6.0
[     3.921] (II) Loading extension DRI2
[     3.921] (==) Matched intel as autoconfigured driver 0
[     3.921] (==) Matched vesa as autoconfigured driver 1
[     3.921] (==) Matched fbdev as autoconfigured driver 2
[     3.921] (==) Assigned the driver to the xf86ConfigLayout
[     3.921] (II) LoadModule: "intel"
[     3.921] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     3.925] (II) Module intel: vendor="X.Org Foundation"
[     3.925] 	compiled for 1.11.3, module version = 2.17.0
[     3.925] 	Module class: X.Org Video Driver
[     3.925] 	ABI class: X.Org Video Driver, version 11.0
[     3.925] (II) LoadModule: "vesa"
[     3.925] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     3.926] (II) Module vesa: vendor="X.Org Foundation"
[     3.926] 	compiled for 1.11.3, module version = 2.3.0
[     3.926] 	Module class: X.Org Video Driver
[     3.926] 	ABI class: X.Org Video Driver, version 11.0
[     3.926] (II) LoadModule: "fbdev"
[     3.926] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     3.927] (II) Module fbdev: vendor="X.Org Foundation"
[     3.927] 	compiled for 1.11.3, module version = 0.4.2
[     3.927] 	ABI class: X.Org Video Driver, version 11.0
[     3.927] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[     3.927] (II) VESA: driver for VESA chipsets: vesa
[     3.927] (II) FBDEV: driver for framebuffer: fbdev
[     3.927] (++) using VT number 7

[     3.930] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     3.930] (WW) Falling back to old probe method for vesa
[     3.930] (WW) Falling back to old probe method for fbdev
[     3.930] (II) Loading sub module "fbdevhw"
[     3.930] (II) LoadModule: "fbdevhw"
[     3.930] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     3.931] (II) Module fbdevhw: vendor="X.Org Foundation"
[     3.931] 	compiled for 1.11.3, module version = 0.0.2
[     3.931] 	ABI class: X.Org Video Driver, version 11.0
[     3.931] drmOpenDevice: node name is /dev/dri/card0
[     3.931] drmOpenDevice: open result is 9, (OK)
[     3.931] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[     3.931] drmOpenDevice: node name is /dev/dri/card0
[     3.931] drmOpenDevice: open result is 9, (OK)
[     3.931] drmOpenByBusid: drmOpenMinor returns 9
[     3.931] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[     3.931] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[     3.931] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[     3.931] (==) intel(0): RGB weight 888
[     3.931] (==) intel(0): Default visual is TrueColor
[     3.931] (II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
[     3.931] (--) intel(0): Chipset: "945GM"
[     3.932] (**) intel(0): Relaxed fencing disabled
[     3.932] (**) intel(0): Wait on SwapBuffers? enabled
[     3.932] (**) intel(0): Triple buffering? enabled
[     3.932] (**) intel(0): Framebuffer tiled
[     3.932] (**) intel(0): Pixmaps tiled
[     3.932] (**) intel(0): 3D buffers tiled
[     3.932] (**) intel(0): SwapBuffers wait enabled
[     3.932] (==) intel(0): video overlay key set to 0x101fe
[     3.932] (II) intel(0): Output LVDS1 has no monitor section
[     3.932] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[     3.964] (II) intel(0): Output VGA1 has no monitor section
[     3.964] (II) intel(0): EDID for output LVDS1
[     3.964] (II) intel(0): Manufacturer: LEN  Model: 4002  Serial#: 0
[     3.964] (II) intel(0): Year: 2006  Week: 0
[     3.964] (II) intel(0): EDID Version: 1.3
[     3.964] (II) intel(0): Digital Display Input
[     3.964] (II) intel(0): Max Image Size [cm]: horiz.: 25  vert.: 18
[     3.964] (II) intel(0): Gamma: 2.20
[     3.964] (II) intel(0): DPMS capabilities: StandBy Suspend Off
[     3.964] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     3.964] (II) intel(0): First detailed timing is preferred mode
[     3.964] (II) intel(0): redX: 0.572 redY: 0.332   greenX: 0.308 greenY: 0.536
[     3.964] (II) intel(0): blueX: 0.149 blueY: 0.157   whiteX: 0.305 whiteY: 0.329
[     3.964] (II) intel(0): Supported established timings:
[     3.964] (II) intel(0): 640x480@60Hz
[     3.964] (II) intel(0): 800x600@60Hz
[     3.964] (II) intel(0): 1024x768@60Hz
[     3.964] (II) intel(0): Manufacturer's mask: 0
[     3.964] (II) intel(0): Supported detailed timing:
[     3.964] (II) intel(0): clock: 65.0 MHz   Image Size:  245 x 184 mm
[     3.964] (II) intel(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
[     3.964] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
[     3.964] (II) intel(0): Unknown vendor-specific block f
[     3.964] (II) intel(0):  HV121X03-100
[     3.964] (II) intel(0): EDID (in hex):
[     3.964] (II) intel(0): 	00ffffffffffff0030ae024000000000
[     3.964] (II) intel(0): 	0010010380191278ea8d5192554e8926
[     3.964] (II) intel(0): 	284e5421080001010101010101010101
[     3.964] (II) intel(0): 	01010101010164190040410026301888
[     3.964] (II) intel(0): 	3600f5b8000000180000001000000000
[     3.964] (II) intel(0): 	000000000000000000000000000f0061
[     3.964] (II) intel(0): 	433c00000013020009e50000000000fe
[     3.964] (II) intel(0): 	0048563132315830332d3130300a005c
[     3.964] (II) intel(0): EDID vendor "LEN", prod id 16386
[     3.964] (II) intel(0): Printing DDC gathered Modelines:
[     3.964] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[     3.964] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[     3.964] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[     3.964] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[     3.964] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[     3.965] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[     3.965] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[     3.965] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[     3.965] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[     3.965] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[     3.965] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[     3.965] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[     3.965] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[     3.965] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[     3.965] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[     3.965] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[     3.965] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[     3.965] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[     3.965] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[     3.965] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[     3.965] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[     3.965] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[     3.965] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[     3.965] (II) intel(0): Printing probed modes for output LVDS1
[     3.965] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[     3.965] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[     3.965] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[     3.965] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[     3.965] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[     3.996] (II) intel(0): EDID for output VGA1
[     3.996] (II) intel(0): Output LVDS1 connected
[     3.996] (II) intel(0): Output VGA1 disconnected
[     3.996] (II) intel(0): Using exact sizes for initial modes
[     3.996] (II) intel(0): Output LVDS1 using initial mode 1024x768
[     3.996] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     3.996] (II) intel(0): Kernel page flipping support detected, enabling
[     3.996] (**) intel(0): Display dimensions: (250, 180) mm
[     3.996] (**) intel(0): DPI set to (104, 108)
[     3.996] (II) Loading sub module "fb"
[     3.996] (II) LoadModule: "fb"
[     3.996] (II) Loading /usr/lib/xorg/modules/libfb.so
[     3.997] (II) Module fb: vendor="X.Org Foundation"
[     3.997] 	compiled for 1.11.3, module version = 1.0.0
[     3.997] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     3.997] (II) Loading sub module "dri2"
[     3.997] (II) LoadModule: "dri2"
[     3.998] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     3.998] (II) Module dri2: vendor="X.Org Foundation"
[     3.998] 	compiled for 1.11.3, module version = 1.2.0
[     3.998] 	ABI class: X.Org Server Extension, version 6.0
[     3.998] (II) UnloadModule: "vesa"
[     3.998] (II) Unloading vesa
[     3.998] (II) UnloadModule: "fbdev"
[     3.998] (II) Unloading fbdev
[     3.998] (II) UnloadModule: "fbdevhw"
[     3.998] (II) Unloading fbdevhw
[     3.998] (==) Depth 24 pixmap format is 32 bpp
[     3.998] (II) intel(0): [DRI2] Setup complete
[     3.998] (II) intel(0): [DRI2]   DRI driver: i915
[     3.998] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[     4.003] (II) UXA(0): Driver registered support for the following operations:
[     4.003] (II)         solid
[     4.003] (II)         copy
[     4.003] (II)         composite (RENDER acceleration)
[     4.003] (II)         put_image
[     4.003] (II)         get_image
[     4.003] (==) intel(0): Backing store disabled
[     4.003] (==) intel(0): Silken mouse enabled
[     4.003] (II) intel(0): Initializing HW Cursor
[     4.016] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     4.019] (==) intel(0): DPMS enabled
[     4.019] (==) intel(0): Intel XvMC decoder disabled
[     4.019] (II) intel(0): Set up textured video
[     4.019] (II) intel(0): Set up overlay video
[     4.019] (II) intel(0): direct rendering: DRI2 Enabled
[     4.019] (==) intel(0): hotplug detection: "enabled"
[     4.019] (--) RandR disabled
[     4.019] (II) Initializing built-in extension Generic Event Extension
[     4.019] (II) Initializing built-in extension SHAPE
[     4.019] (II) Initializing built-in extension MIT-SHM
[     4.019] (II) Initializing built-in extension XInputExtension
[     4.019] (II) Initializing built-in extension XTEST
[     4.019] (II) Initializing built-in extension BIG-REQUESTS
[     4.019] (II) Initializing built-in extension SYNC
[     4.019] (II) Initializing built-in extension XKEYBOARD
[     4.019] (II) Initializing built-in extension XC-MISC
[     4.019] (II) Initializing built-in extension SECURITY
[     4.019] (II) Initializing built-in extension XINERAMA
[     4.019] (II) Initializing built-in extension XFIXES
[     4.019] (II) Initializing built-in extension RENDER
[     4.019] (II) Initializing built-in extension RANDR
[     4.019] (II) Initializing built-in extension COMPOSITE
[     4.020] (II) Initializing built-in extension DAMAGE
[     4.053] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     4.053] (II) AIGLX: enabled GLX_INTEL_swap_event
[     4.053] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[     4.053] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     4.053] (II) AIGLX: Loaded and initialized i915
[     4.054] (II) GLX: Initialized DRI2 GL provider for screen 0
[     4.054] (II) intel(0): Setting screen physical size to 270 x 203
[     4.071] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     4.077] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[     4.077] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     4.077] (II) LoadModule: "evdev"
[     4.078] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     4.080] (II) Module evdev: vendor="X.Org Foundation"
[     4.080] 	compiled for 1.11.3, module version = 2.7.0
[     4.080] 	Module class: X.Org XInput Driver
[     4.080] 	ABI class: X.Org XInput driver, version 16.0
[     4.080] (II) Using input driver 'evdev' for 'Power Button'
[     4.080] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     4.080] (**) Power Button: always reports core events
[     4.080] (**) evdev: Power Button: Device: "/dev/input/event2"
[     4.080] (--) evdev: Power Button: Vendor 0 Product 0x1
[     4.080] (--) evdev: Power Button: Found keys
[     4.080] (II) evdev: Power Button: Configuring as keyboard
[     4.080] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[     4.080] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     4.080] (**) Option "xkb_rules" "evdev"
[     4.080] (**) Option "xkb_model" "pc105"
[     4.080] (**) Option "xkb_layout" "gb"
[     4.084] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[     4.085] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[     4.085] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     4.085] (II) Using input driver 'evdev' for 'Video Bus'
[     4.085] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     4.086] (**) Video Bus: always reports core events
[     4.086] (**) evdev: Video Bus: Device: "/dev/input/event4"
[     4.086] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     4.086] (--) evdev: Video Bus: Found keys
[     4.086] (II) evdev: Video Bus: Configuring as keyboard
[     4.086] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4/event4"
[     4.086] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     4.086] (**) Option "xkb_rules" "evdev"
[     4.086] (**) Option "xkb_model" "pc105"
[     4.086] (**) Option "xkb_layout" "gb"
[     4.087] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[     4.087] (II) No input driver specified, ignoring this device.
[     4.087] (II) This device may have been added with another device file.
[     4.087] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[     4.087] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[     4.087] (II) Using input driver 'evdev' for 'Sleep Button'
[     4.087] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     4.087] (**) Sleep Button: always reports core events
[     4.087] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[     4.087] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[     4.087] (--) evdev: Sleep Button: Found keys
[     4.087] (II) evdev: Sleep Button: Configuring as keyboard
[     4.087] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[     4.087] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[     4.087] (**) Option "xkb_rules" "evdev"
[     4.087] (**) Option "xkb_model" "pc105"
[     4.087] (**) Option "xkb_layout" "gb"
[     4.089] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[     4.089] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     4.089] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     4.089] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     4.089] (**) AT Translated Set 2 keyboard: always reports core events
[     4.089] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[     4.089] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     4.089] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     4.089] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     4.089] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[     4.089] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[     4.089] (**) Option "xkb_rules" "evdev"
[     4.089] (**) Option "xkb_model" "pc105"
[     4.089] (**) Option "xkb_layout" "gb"
[     4.090] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event6)
[     4.090] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[     4.090] (**) TPPS/2 IBM TrackPoint: Applying InputClass "trackpoint catchall"
[     4.090] (II) Using input driver 'evdev' for 'TPPS/2 IBM TrackPoint'
[     4.090] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     4.090] (**) TPPS/2 IBM TrackPoint: always reports core events
[     4.090] (**) evdev: TPPS/2 IBM TrackPoint: Device: "/dev/input/event6"
[     4.090] (--) evdev: TPPS/2 IBM TrackPoint: Vendor 0x2 Product 0xa
[     4.090] (--) evdev: TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[     4.090] (--) evdev: TPPS/2 IBM TrackPoint: Found relative axes
[     4.090] (--) evdev: TPPS/2 IBM TrackPoint: Found x and y relative axes
[     4.090] (II) evdev: TPPS/2 IBM TrackPoint: Configuring as mouse
[     4.090] (**) Option "Emulate3Buttons" "true"
[     4.090] (**) Option "EmulateWheel" "true"
[     4.090] (**) Option "EmulateWheelButton" "2"
[     4.090] (**) Option "YAxisMapping" "4 5"
[     4.090] (**) evdev: TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[     4.090] (**) Option "XAxisMapping" "6 7"
[     4.090] (**) evdev: TPPS/2 IBM TrackPoint: XAxisMapping: buttons 6 and 7
[     4.090] (**) evdev: TPPS/2 IBM TrackPoint: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     4.090] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[     4.090] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE, id 10)
[     4.090] (II) evdev: TPPS/2 IBM TrackPoint: initialized for relative axes.
[     4.091] (**) TPPS/2 IBM TrackPoint: (accel) keeping acceleration scheme 1
[     4.091] (**) TPPS/2 IBM TrackPoint: (accel) acceleration profile 0
[     4.091] (**) TPPS/2 IBM TrackPoint: (accel) acceleration factor: 2.000
[     4.091] (**) TPPS/2 IBM TrackPoint: (accel) acceleration threshold: 4
[     4.091] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse0)
[     4.091] (II) No input driver specified, ignoring this device.
[     4.091] (II) This device may have been added with another device file.
[     4.094] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event5)
[     4.094] (**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
[     4.094] (II) Using input driver 'evdev' for 'ThinkPad Extra Buttons'
[     4.094] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     4.094] (**) ThinkPad Extra Buttons: always reports core events
[     4.094] (**) evdev: ThinkPad Extra Buttons: Device: "/dev/input/event5"
[     4.095] (--) evdev: ThinkPad Extra Buttons: Vendor 0x17aa Product 0x5054
[     4.095] (--) evdev: ThinkPad Extra Buttons: Found keys
[     4.095] (II) evdev: ThinkPad Extra Buttons: Configuring as keyboard
[     4.095] (**) Option "config_info" "udev:/sys/devices/platform/thinkpad_acpi/input/input5/event5"
[     4.095] (II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD, id 11)
[     4.095] (**) Option "xkb_rules" "evdev"
[     4.095] (**) Option "xkb_model" "pc105"
[     4.095] (**) Option "xkb_layout" "gb"
[     4.096] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS4)
[     4.096] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[     4.096] (II) LoadModule: "wacom"
[     4.096] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[     4.098] (II) Module wacom: vendor="X.Org Foundation"
[     4.098] 	compiled for 1.11.3, module version = 0.14.0
[     4.098] 	Module class: X.Org XInput Driver
[     4.098] 	ABI class: X.Org XInput driver, version 16.0
[     4.098] (II) Using input driver 'wacom' for 'Serial Wacom Tablet'
[     4.098] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[     4.098] (**) Serial Wacom Tablet: always reports core events
[     4.098] (**) Option "Device" "/dev/ttyS4"
[     4.098] (**) Option "StopBits" "1"
[     4.098] (**) Option "DataBits" "8"
[     4.098] (**) Option "Parity" "None"
[     4.098] (**) Option "Vmin" "1"
[     4.098] (**) Option "Vtime" "10"
[     4.098] (**) Option "FlowControl" "Xoff"
[     4.099] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[     4.099] (II) Serial Wacom Tablet: other types will be automatically added.
[     7.605] (WW) Serial Wacom Tablet stylus: Waited too long for answer (failed after 3 tries).
[     7.605] (II) Serial Wacom Tablet stylus: serial tablet id 0x93.
[     7.605] (--) Serial Wacom Tablet stylus: using pressure threshold of 27 for button 1
[     7.605] (--) Serial Wacom Tablet stylus: Wacom General ISDV4 tablet maxX=24576 maxY=18432 maxZ=255 resX=100000 resY=100000  tilt=disabled
[     7.605] (II) Serial Wacom Tablet stylus: hotplugging dependent devices.
[     7.605] (EE) Serial Wacom Tablet stylus: Invalid type 'cursor' for this device.
[     7.606] (EE) Serial Wacom Tablet stylus: Invalid type 'pad' for this device.
[     7.606] (II) Serial Wacom Tablet stylus: hotplugging completed.
[     7.606] (**) Option "config_info" "udev:/sys/devices/pnp0/00:0b/tty/ttyS4"
[     7.606] (II) XINPUT: Adding extended input device "Serial Wacom Tablet stylus" (type: STYLUS, id 12)
[     7.606] (**) Serial Wacom Tablet stylus: (accel) keeping acceleration scheme 1
[     7.606] (**) Serial Wacom Tablet stylus: (accel) acceleration profile 0
[     7.606] (**) Serial Wacom Tablet stylus: (accel) acceleration factor: 2.000
[     7.606] (**) Serial Wacom Tablet stylus: (accel) acceleration threshold: 4
[     7.607] (**) Option "BaudRate" "38400"
[     7.613] (**) Serial Wacom Tablet eraser: Applying InputClass "Wacom serial class"
[     7.613] (II) Using input driver 'wacom' for 'Serial Wacom Tablet eraser'
[     7.613] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[     7.613] (**) Serial Wacom Tablet eraser: always reports core events
[     7.613] (**) Option "Device" "/dev/ttyS4"
[     7.613] (**) Option "Type" "eraser"
[     7.613] (**) Option "BaudRate" "38400"
[     7.613] (**) Option "StopBits" "1"
[     7.613] (**) Option "DataBits" "8"
[     7.613] (**) Option "Parity" "None"
[     7.613] (**) Option "Vmin" "1"
[     7.613] (**) Option "Vtime" "10"
[     7.613] (**) Option "FlowControl" "Xoff"
[     7.613] (--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet maxX=24576 maxY=18432 maxZ=255 resX=100000 resY=100000  tilt=disabled
[     7.613] (**) Option "config_info" "udev:/sys/devices/pnp0/00:0b/tty/ttyS4"
[     7.613] (II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER, id 13)
[     7.614] (**) Serial Wacom Tablet eraser: (accel) keeping acceleration scheme 1
[     7.614] (**) Serial Wacom Tablet eraser: (accel) acceleration profile 0
[     7.614] (**) Serial Wacom Tablet eraser: (accel) acceleration factor: 2.000
[     7.614] (**) Serial Wacom Tablet eraser: (accel) acceleration threshold: 4
[     7.614] (**) Serial Wacom Tablet touch: Applying InputClass "Wacom serial class"
[     7.614] (II) Using input driver 'wacom' for 'Serial Wacom Tablet touch'
[     7.614] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[     7.614] (**) Serial Wacom Tablet touch: always reports core events
[     7.614] (**) Option "Device" "/dev/ttyS4"
[     7.614] (**) Option "Type" "touch"
[     7.614] (**) Option "BaudRate" "38400"
[     7.614] (**) Option "StopBits" "1"
[     7.614] (**) Option "DataBits" "8"
[     7.614] (**) Option "Parity" "None"
[     7.614] (**) Option "Vmin" "1"
[     7.614] (**) Option "Vtime" "10"
[     7.614] (**) Option "FlowControl" "Xoff"
[     7.614] (--) Serial Wacom Tablet touch: Wacom General ISDV4 tablet maxX=24576 maxY=18432 maxZ=255 resX=100000 resY=100000  tilt=disabled
[     7.615] (**) Option "config_info" "udev:/sys/devices/pnp0/00:0b/tty/ttyS4"
[     7.615] (II) XINPUT: Adding extended input device "Serial Wacom Tablet touch" (type: TOUCH, id 14)
[     7.615] (**) Serial Wacom Tablet touch: (accel) keeping acceleration scheme 1
[     7.615] (**) Serial Wacom Tablet touch: (accel) acceleration profile 0
[     7.615] (**) Serial Wacom Tablet touch: (accel) acceleration factor: 2.000
[     7.615] (**) Serial Wacom Tablet touch: (accel) acceleration threshold: 4
[     8.149] (II) intel(0): EDID vendor "LEN", prod id 16386
[     8.149] (II) intel(0): Printing DDC gathered Modelines:
[     8.149] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[     8.149] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[     8.149] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[     8.671] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[     8.676] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[     9.267] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.528] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.535] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.540] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.547] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.552] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.557] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.562] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.567] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.585] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.591] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.599] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.640] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.646] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.656] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.669] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.679] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.687] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.695] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.701] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.711] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.727] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.735] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.743] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.752] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.763] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.768] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.776] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.783] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.791] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[     9.803] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.169] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.194] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.199] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.210] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.215] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.219] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.224] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.229] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.233] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.238] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.257] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.269] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.281] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.286] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.294] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.299] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.303] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.309] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.314] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.318] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.323] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.329] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.333] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.338] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.344] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.348] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.353] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.359] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.363] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.368] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    10.372] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    11.075] (II) intel(0): EDID vendor "LEN", prod id 16386
[    11.075] (II) intel(0): Printing DDC gathered Modelines:
[    11.075] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    11.075] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    11.075] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    30.172] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    32.463] (II) intel(0): EDID vendor "LEN", prod id 16386
[    32.464] (II) intel(0): Printing DDC gathered Modelines:
[    32.464] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    32.464] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    32.464] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    33.036] (II) intel(0): EDID vendor "LEN", prod id 16386
[    33.036] (II) intel(0): Printing DDC gathered Modelines:
[    33.036] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    33.036] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    33.036] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    33.734] (II) intel(0): EDID vendor "LEN", prod id 16386
[    33.734] (II) intel(0): Printing DDC gathered Modelines:
[    33.734] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    33.734] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    33.734] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    40.115] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[    42.816] (WW) Serial Wacom Tablet touch: bad data at 1 v=91 l=5
[    53.447] (II) intel(0): EDID vendor "LEN", prod id 16386
[    53.447] (II) intel(0): Printing DDC gathered Modelines:
[    53.447] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    53.447] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    53.447] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   278.324] (WW) Serial Wacom Tablet touch: bad data at 1 v=91 l=5
[   280.030] (WW) Serial Wacom Tablet touch: bad data at 1 v=91 l=5
[   281.878] (WW) Serial Wacom Tablet touch: bad data at 1 v=91 l=5
[   281.902] (WW) Serial Wacom Tablet touch: bad data at 1 v=91 l=5
[   284.074] (WW) Serial Wacom Tablet touch: bad data at 1 v=91 l=5
[   390.410] (WW) Serial Wacom Tablet touch: bad data at 1 v=91 l=5
[   391.241] (WW) Serial Wacom Tablet touch: bad data at 1 v=91 l=5
[   401.637] (WW) Serial Wacom Tablet touch: bad data at 1 v=91 l=5
[   403.710] (WW) Serial Wacom Tablet touch: bad data at 1 v=91 l=5
[   460.147] (WW) Serial Wacom Tablet touch: bad data at 1 v=91 l=5
[   462.279] (WW) Serial Wacom Tablet touch: bad data at 1 v=91 l=5
[   464.082] (WW) Serial Wacom Tablet touch: bad data at 1 v=91 l=5
[   465.955] (WW) Serial Wacom Tablet touch: bad data at 1 v=91 l=5
[  1694.072] (WW) Serial Wacom Tablet touch: bad data at 1 v=91 l=5
[  1695.156] (WW) Serial Wacom Tablet touch: bad data at 1 v=91 l=5
[  1695.869] (WW) Serial Wacom Tablet touch: bad data at 1 v=91 l=5
[  2045.574] (WW) Serial Wacom Tablet touch: bad data at 1 v=91 l=5

i will have a look tomorrow at the scripts you suggested (it's midnight here so it will have to wait) and will post

---

### Post by Favux on 2012-09-18
Sure.  Alright, a fresh start tomorrow.

What coordinates do you get for touch with xinput_calibrator?  Because Xorg.0.log is giving the same coordinates as the stylus and eraser:
```
[ 7.614] (--) Serial Wacom Tablet touch: Wacom General ISDV4 tablet maxX=24576 maxY=18432 maxZ=255 resX=100000 resY=100000 tilt=disabled
```
Which may not be correct.

Also you're getting an error message:
```
[ 42.816] (WW) Serial Wacom Tablet touch: bad data at 1 v=91 l=5
```
So we might want to look at a few things and maybe install an updated xf86-input-wacom.

---

### Post by mmoalem on 2012-09-19
hi again. i have to say that i really appreciate your kind help. you are defently going out of your way here. thanks a million!

i'm at work now but will keep an eye on the thread for your replies

picked up these numbers:
> xsetwacom set "Serial Wacom Tablet touch" Area 25 50 950 980
from this page:
[http://ubuntuforums.org/archive/index.php/t-1833955.html](http://ubuntuforums.org/archive/index.php/t-1833955.html)

these numbers seems to be far from the xorg log but they do seem to be fairly close once set...

---

### Post by Favux on 2012-09-19
Nice find.

The touch screen is a separate device that is sandwhiched with the digitizer and it should have a much lower resolution than the Wacom digitizer.  So those numbers make much more sense.  From the old xsetwacom.sh's for the X200t and Toshiba 750 the coordinates are:
```
#xsetwacom set 13 topy "215"
#xsetwacom set 13 topx "140"
#xsetwacom set 13 bottomy "3969"
#xsetwacom set 13 bottomx "4028"
```
So maybe intended to be?
```
#xsetwacom set 13 topy "0"
#xsetwacom set 13 topx "0"
#xsetwacom set 13 bottomy "4028"
#xsetwacom set 13 bottomx "4028"
```
While the digitizer calibration is usually good out of the box it seems that all of the tablet PCs with touch need their touch calibrated.

Please let me know if you refine those anymore.

---

### Post by mmoalem on 2012-09-19
hi - i assume i should put these lines into xsetwacom.sh but before i do i would like to understand couple of things

as my stylus works fine can i just comment out the stylus lines in the script? (so it wont interfere with the already settings?

also what is the best way to load and reload the script everytime i change values? i assume i dont need to reboot the laptop everytime...

---

### Post by Favux on 2012-09-19
> as my stylus works fine can i just comment out the stylus lines in the script? (so it wont interfere with the already settings?
Yes.  Those lines are there to show you what you can adjust if you want to.  There is no reason to apply an xsetwacom command if the default setting is already working for you.  But by keeping them commented out you have a convienent list of what is available.  And I usually tried to put the default for the parameter in too.
> also what is the best way to load and reload the script everytime i change values? i assume i dont need to reboot the laptop everytime... 
xsetwacom commands are runtime so you could just run the script from a terminal any time you wanted to reapply it.  To make it convienent I put the auto-start script into a launcher that I can just double click on if I want to run it again.  The path in the launcher is to the same auto-start script.  Plus you can use a "descriptive" icon for the launcher.

---

### Post by mmoalem on 2012-09-20
hi again

so i have got the calibration working quite well
had some problems when i put the numbers in this format:
> xsetwacom set "Serial Wacom Tablet touch" topx "25"
xsetwacom set "Serial Wacom Tablet touch" topy "50"
xsetwacom set "Serial Wacom Tablet touch" bottomx "950"
xsetwacom set "Serial Wacom Tablet touch" bottomy "980"

with calibration still way off but puting it in this format
> xsetwacom set "Serial Wacom Tablet touch" Area 25 50 950 980 it's way closer - not sure why it works one way and not the other?

anyway - will try to refine these when as i go along

so now will look at magick-rotation but will also need to find a way to make the hardware keys on the screen bezel work - any idea how to assign commands to these?

also for some reason when running xbmc touch does not work at all...

---

### Post by Favux on 2012-09-20
The topX & Y and bottom X & Y were the old xsetwacom parameters and have been replaced by the Area parameter.  That's why only Area works now with recent versions of xsetwacom.  To get version enter:
```
xsetwacom -V
```
I talked Peter into including a table in the code so when you put in an old parameter in the terminal you should get an error message that tells you the new parameter name.  A bunch were changed.  Or I made a little table:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#Table_of_New_Parameter_Names](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#Table_of_New_Parameter_Names)

Good let me know the refined values when you get them.  I've bookmarked them now so I have them.  Not sure why I didn't do that before.  Probably have a X60t xorg.conf somewhere (or that .fdi file you linked to) that has them and I just can't find it now.
> so now will look at magick-rotation but will also need to find a way to make the hardware keys on the screen bezel work - any idea how to assign commands to these?
Silly things seem to change every release as the upstream developers change stuff in the key code chain all the time.  Or it seems like they do anyway.  Thinkwiki is a good resource:  [http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)  Going to the Thinkpad Models page and then X series gets us:  [http://www.thinkwiki.org/wiki/Category:X_Series](http://www.thinkwiki.org/wiki/Category:X_Series)  Then on the X60 tablet page:  [http://www.thinkwiki.org/wiki/Category:X60_Tablet](http://www.thinkwiki.org/wiki/Category:X60_Tablet)  we follow the link to:  [http://www.thinkwiki.org/wiki/Tablet_Hardware_Buttons](http://www.thinkwiki.org/wiki/Tablet_Hardware_Buttons)

But that's two years old.  I have some more stuff on bezel buttons on the [Rotation HOW TO]("http://ubuntuforums.org/showthread.php?t=996830") (or the [updated version]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110395")) I already linked you to, in appendix 2 and adjacent.  Googling around will probably turn up something.

Sorry, don't know anything about xbmc.  That's a cross platform media player?

---

### Post by mmoalem on 2012-09-21
quick question re auto start - it seems that the xsetwacom.sh is loading after login - any idea how to load so it is available at the gdm login page (so i can login in tablet mode)?

---

### Post by Favux on 2012-09-21
Short answer is no.

Long answer is the X Server starts after you login, that's why the tablet isn't available at the login screen.  I think.  You're missing the X half of the Wacom driver.  Since the mouse does work there must be some way to cobble together a tablet pen driver for whatever windowing system is running at login.  Piggyback on the mouse code?  After all you don't need pressure then or other fancy features.  Or super accuracy at that point.  Never looked into it.

---

### Post by mmoalem on 2012-09-24
hi again- hope you had good weekend.

just to clarify something. touch is available at login it is just uncalibrated - i assume x is fully running for the gdm login but the script is run on login i guess because it is user specific

i assume it needs to be placed somewhere else than user home folder for it to be called upon through the boot process...

---

### Post by Favux on 2012-09-24
Sounds like I was wrond and X does come up with the login screen before the gui starts.  If that's true of the Wacom X driver stuff then I suppose it would be true of xsetwacom.  I read something about an X200t that seemed to indicate stylus and touch available at login over the weekend.

Which makes me wonder if adding the xsetwacom command to rc.local at /etc would work.  Could try I suppose:
```
gksudo gedit /etc/rc.local
```
and hope nothing breaks.  Be prepared to boot in Recovery mode.  Place the command above the **exit 0** line you'll see.  Don't quite know where rc.local is in the boot chain.  Earlier than a startup script anyway.  Maybe too early for xsetwacom to work?

---

### Post by maviperu on 2013-02-28
> **Favux said:**
> Single finger touch for a tablet PC should be Absolute Mode also. Try:
```
xsetwacom get "Serial Wacom Tablet touch" Mode
```
and see if it returns Absolute. Either way then run:
```
xsetwacom set "Serial Wacom Tablet touch" Mode Absolute
```
We'll see if that helps. I'm wondering/guessing if the GNOME Wacom tablet applet in System Settings is messing up your touch and setting it in Relative Mode.

Wow! Thank you so much!! :D

That was easy and worked perfectly

I am on a Fujitsu TH700 and now pen and touch both work perfectly

Thanks again

---

### Post by mmoalem on 2013-03-17
hi again - been wondering if there is a way to assign one of the buttons on side of the screen to act as right click as i have no way to right click using finger touch...

---

### Post by Favux on 2013-03-17
I wonder if you can do that using Universal Access in System Settings?  Go to the Pointing and Clicking tab and turn on Simulated Secondary Click.  You may need to vary the delay.  Then hold your finger down and see if you get a right click.

---

### Post by mmoalem on 2013-03-17
> **Favux said:**
> I wonder if you can do that using Universal Access in System Settings?  Go to the Pointing and Clicking tab and turn on Simulated Secondary Click.  You may need to vary the delay.  Then hold your finger down and see if you get a right click.

nice idea but does not make a difference... there must be a way to map this to a hardware key...


EDIT: spoke too early. it does work upon lifting the finger so thank for that... mind you a hardware key might be more convnient if i can make it work.


EDIT2: works randomly. selecting a word in a web page in chrome than trying to 'right click' on usually loose the 'selection  highlight' as if another click was performed in between...

---

### Post by Favux on 2013-03-17
You might just want to play with the delay time a bit.

Well the tablet PC Rotation HOW TO talks about using the bezel keys:  [http://ubuntuforums.org/showthread.php?t=996830](http://ubuntuforums.org/showthread.php?t=996830)

Then you could use xdotool or some such to get the right click I suppose, if you can't assign it to 3 (right click) directly.

---

