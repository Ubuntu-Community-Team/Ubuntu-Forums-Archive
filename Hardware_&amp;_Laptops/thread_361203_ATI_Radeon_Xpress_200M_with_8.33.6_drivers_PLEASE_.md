---
title: "ATI Radeon Xpress 200M with 8.33.6 drivers PLEASE HELP"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by uv256 on 2007-02-14
greetings,

I'm running the latest ATI drivers on Suse 10.2
I have the ATI Technologies Inc RC410 [Radeon Xpress 200M]
everything seems to be working fine except very slow performance I'm running beryl as my window manager and it's running but when doing multi tasking everything is very slow.... is there anyway I could speed things up?

also I have the following errors:
when executing fgl_glxgears I get the following:

Using GLX_SGIX_pbuffer
Xlib: extension "XFree86-DRI" missing on display ":0.0".
Error: couldn't get fbconfig

and glxinfo | grep direct
Xlib: extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No

but when I cat Xorg.0.log | grep DRI
(II) Loading extension XFree86-DRI
(**) fglrx(0): Option "NoDRI" "no"
(**) fglrx(0): NoDRI = NO
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): [DRI] installation complete

so I'm a bit confused can anyone help me to resolve these errors please....

also when I cat Xorg.0.log | grep "(EE)"
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

but this error is because the drivers don't support AIGLX yet... so it's not relevant to my problem ... I could fix this error by disabling AIGLX in xorg.conf... but when I do that my system sometimes hangs for some reason so I rather keep it there....

when I installed the driver I got the following errors:
stalled the driver I got the following errors:

Preparing...                ########################################### [100%]
   1:fglrx_7_1_0_SUSE102    ########################################### [100%]
/usr/src/kernel-modules/fglrx /
rm: cannot remove `Modules.symvers': No such file or directory
rm: cannot remove `*.o': No such file or directory
rm: cannot remove `*.ko': No such file or directory
rm: cannot remove `*.mod.*': No such file or directory
make: Entering directory `/usr/src/linux-2.6.18.2-34-obj/i386/bigsmp'
make -C ../../../linux-2.6.18.2-34 O=../linux-2.6.18.2-34-obj/i386/bigsmp
  LD      /usr/src/kernel-modules/fglrx/built-in.o
  CC [M]  /usr/src/kernel-modules/fglrx/firegl_public.o
/usr/src/kernel-modules/fglrx/firegl_public.c:468: warning: initialization from 
incompatible pointer type
/usr/src/kernel-modules/fglrx/firegl_public.c: In function $-1òøfiregl_stub_openòù:
/usr/src/kernel-modules/fglrx/firegl_public.c:591: warning: assignment discards 
qualifiers from pointer target type
/usr/src/kernel-modules/fglrx/firegl_public.c: In function $-1òø__ke_smp_call_functi
on$-1òù:
/usr/src/kernel-modules/fglrx/firegl_public.c:4024: warning: passing argument 1 
of $-1òøsmp_call_functionòù from incompatible pointer type
/usr/src/kernel-modules/fglrx/firegl_public.c: In function $-1òøKAS_ExecuteAtLevelòù:
/usr/src/kernel-modules/fglrx/firegl_public.c:4449: warning: $-1òøflagsòù may be used
 uninitialized in this function
 LD [M]  /usr/src/kernel-modules/fglrx/fglrx.o
  Building modules, stage 2.
  MODPOST
WARNING: could not find /usr/src/kernel-modules/fglrx/.libfglrx_ip.a.GCC4.cmd fo
r /usr/src/kernel-modules/fglrx/libfglrx_ip.a.GCC4
  CC      /usr/src/kernel-modules/fglrx/fglrx.mod.o
  LD [M]  /usr/src/kernel-modules/fglrx/fglrx.ko
make: Leaving directory `/usr/src/linux-2.6.18.2-34-obj/i386/bigsmp'
make: Entering directory `/usr/src/linux-2.6.18.2-34-obj/i386/bigsmp'
make -C ../../../linux-2.6.18.2-34 O=../linux-2.6.18.2-34-obj/i386/bigsmp module
s_install
  INSTALL /usr/src/kernel-modules/fglrx/fglrx.ko
  DEPMOD  2.6.18.2-34-bigsmp
make: Leaving directory `/usr/src/linux-2.6.18.2-34-obj/i386/bigsmp'

---

### Post by uv256 on 2007-02-17
Ok.... I figured it out... I get this errors because XGL is enabled .... so to get rid of this errors
I have to disable XGL but then all the fun is gone... and from what I understand I can't get 3d accelration
with the open source drivers because it's broken for the Radeon Xpress 200M

So I'm stuck with slow performance

---

### Post by xenblend on 2007-02-17
I too have the radeon xpress 200M on my toshiba satellite and have never noticed any problems with graphics in ubuntu but im on windows right now so i'll give it a looksie next time i boot into ubuntu and see what my logs are telling me.  i think i have 3d acceleration but perhaps i'm wrong.  I am using the 'radeon' driver which is, i believe, the 3d accelerated one.  (the only other one I know of is the 'ati' driver which is open-source and is not accelerated...)  good luck!

xb

---

### Post by xenblend on 2007-02-17
Argh!  So now I'm in Ubuntu and I do NOT have 3D acceleration, even with the 'radeon' driver that I thought was ever so wonderful!  How do I get 3D acceleration going?  I thought I was in the know... :(

---

### Post by lamalex on 2007-02-17
Yah, that's XGL. It's your only option until ATi starts giving us real support. Ive heard some people have it working well, most others don't. Email ATi and tell them to get their act together and support us or we're all going nvidia!

and xenblend, the accelerated drivers are fglrx

---

### Post by xenblend on 2007-02-17
I am downloading the fglrx package from ATI as I type this... thanks for the help!

XB

---

### Post by ctt1wbw on 2007-02-18
In your xorg.conf file, where your screen readings are and the drivers listed there, they can't say radeon or ati, they have to say driver = fglrx, and then you have to disable the loading of aiglx.

Make sure yours looks something like mine:


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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	[SIZE="5"][SIZE="7"][SIZE="6"]**Load  "fglrx"**[/SIZE][/SIZE][/SIZE]
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "ATI Radeon XPress 200m"
	HorizSync    28.0 - 72.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Radeon XPress 200m"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Radeon XPress 200m"
	Monitor    "ATI Radeon XPress 200m"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1440x900"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1440x900"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1440x900"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1440x900"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1440x900"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1440x900"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

Section "ServerFlags"
	Option "AIGLX" "off"
EndSection


I had to add the bolded section at the top to get mine to work on beryl.  Everything is great now.  :)

---

### Post by peacekpr on 2007-02-18
I am using fglrx version 8.32.5 with XGL and Beryl working flawlessly (so it seems).  I, too, have the Xpress 200M video card (except in a Dell Inspiron 1501).  I could not get XGL and Beryl up and running without adding the following lines to my video card device subsection:
```
Option        "BlockSignalsOnLock" "on"
Option       "KernelModuleParm" "locked-userpages=0"
Option       "mtrr" "on"
```

It's probably worth a try to get yours working as well.  Be sure to make a backup of your current xorg.conf file.

Good luck!

---

