---
title: "Suspend with FGLRX + Radeon Xpress 200m"
date: 2007-02-23
forum: Hardware &amp; Laptops
---

### Post by uberbrodt on 2007-02-23
I've been using Debian and Linux for the past 3-4 years or so, partly out of hobby and later for work.  

I decided to give Ubuntu Edgy a try, being very interested in getting better ACPI support (any ACPI support, really) on my Toshiba Satellite M45-s165 with a Radeon Xpress 200m video card.

The install went smoothly and booted with the xorg-ati drivers, but was unable to suspend to ram.  It would go down fine, but would hang with a black screen on startup (cdrom, hard drive, and fans seem to rev up however).  Tried the fglrx drivers that came in the restricted repos, which worked easily with 3d accel but received the same results with suspend.

Followed the Ubuntu guide for installing the ATI bin packages (much easier then on Debian, BTW).   Again, worked fine with 3D accel, but no suspend to ram.

It would be useful to point out at this point that Hibernate(suspend to disk) seems to work fine in all instances.  Haven't had it fail in any of the above driver configurations.

I've mostly been tinkering with the acpi-support file in /etc/default, hoping that I might find the right config there, but nothing yet.  I've tried most of the configurations that people list for my card on these forums and elsewhere, but no progress yet.  Again, Hibernate continues to work throughout all of the changes I've made.

So, I'm stumped.  My only theories at this point are:

1)  Something wrong  with Swap/RAM?
2)  Still incorrect acpi-support settings?
3)  can't imagine that the wireless would affect it, but it's an Atheros chip that runs on the Madwifi drivers.  Never know with proprietary stuff.

Any suggestions or theories would be great.  I'm grateful that Hibernate works, but it mostly whetted my appetite for complete victory ;)  I can post xorg or other files, but they're all pretty stock as I did the install last night.

Thanks in advance

---

### Post by Tn3 on 2007-02-23
I had some similar problems with my mobile x600.
Installed fglrx 8.34.8 and changed  POST_VIDEO to false in /etc/default/acpi-support and now hibernate and suspend works.

---

### Post by uberbrodt on 2007-02-23
Thanks for the reply!  Could you post/e-mail me your acpi-support settings and/or xorg.conf so that I can make sure my settings matched up with yours?  I've fiddled so much with the acpi-support settings that I'm not sure what the defaults were.  It might also help others with the same problem.

---

### Post by Tn3 on 2007-02-23
xorg.conf
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "Device"
	Identifier	"X600"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	VideoRam	65536
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Monitor"
	Identifier	"WXGA"
	Option		"DPMS"
	HorizSync 	31.5 - 50.0
	VertRefresh 	40-90
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"X600"
	Monitor		"WXGA"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
Option "Composite" "disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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


```
/etc/default/acpi-support
```


# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=true


```

---

### Post by uberbrodt on 2007-02-24
I used your settings, but it still locks up with a black screen when I do suspend to ram.  I'm sure some people have gotten my specific card to work, maybe it's a problem with my specific model of laptop?

---

### Post by chadlongstaff on 2007-03-19
I've had a Toshiba Equium M50-192 with an ATI 200m for about 14 months. No combination of drivers I've found allow me to return from suspend without this black screen problem.

---

### Post by tortsto on 2007-03-20
Awesome suspend and hibernate work perfectly for me.  Running fglrx 8.28 on Edgy with kernel 2.6.17-11-generic with my ATI Radeon 9600 Mobility Pro Turbo.

---

### Post by lamalex on 2007-04-13
I'm getting very close, when you were fiddling with settings have you ever woken up, but no keyboard? Your file never forces me to actually go down, it just does the lock-screen function for some reason..

---

### Post by moixa on 2007-04-13
try setting
"VbetoolPost no"
"EnableVbetool no"
in  /etc/hibernate/ram.conf

POST_VIDEO=
in /etc/default/acpi-support

---

### Post by uberbrodt on 2007-04-14
Yeah, I ended up upgrading to the beta release, and everything got kind of screwy.  I haven't messed with the fglrx drivers yet, since I actually need to use the laptop (finals and such).  I'm kind of resigned about ever getting suspend to work; seems like I just lucked out with the worst possible video card for my laptop.

---

