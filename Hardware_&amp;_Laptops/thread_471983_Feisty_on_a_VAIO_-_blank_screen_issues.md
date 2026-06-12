---
title: "Feisty on a VAIO - blank screen issues"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by rsain on 2007-06-12
Have been trying to get my older (2 years) Vaio VGN-S360 up and running with ubuntu desktop. The live CD would never get past the installer options, so I created an alternate. This allowed me to install. Great! Even pulled a wireless dhcp connection during the install! Wow!

Then it tries to boot. 

Displays the splash screen just fine with no boot options modified. After that, a cursor appears about about half a second, the screen flickers, then goes blank. Period.

I've tried several boot options, all making stuff worse, or no change:

acpi=off
vga=0
vga=1
vga=771
acpi=off pnpbios=off noapic noapm 
vga=0 debug -b 3 
failsafe debug -b 3

to name a few....

So I tried booting from the recovery mode kernel (2.6.20-15-generic). This allowed me to use the machine on a command line basis only. However, all of my networking was shot.

The sticker on the box indicates I have a Intel Centrino/ ATI M. Radfeon 9700 (lspci says it's a 9600 though). 

I've been working on this for about 2 days and have tried just about everything I can find in the forums except for installing a new driver (Can't connect to the net when I'm in recovery mode ). 

Any help will be greatly appreciated.

- Ryan

---

### Post by rsain on 2007-06-13
bump

---

### Post by rsain on 2007-06-13
been working through a bunch more options, needless to say, nothing has worked. Here is the most recent test:

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

Still the same thing. After the splashscreen - a flicker and blank. 

WTF?

- Ryan

---

### Post by rsain on 2007-06-13
Just in case this might help. I was able to get the wireless running under recovery mode which allowed me to get all this info off the VAIO. See below for lspci / acpi-support / xorg.conf

[COLOR="DarkRed"]LSPCI Output[/COLOR]
```

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:04.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
02:04.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
02:04.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
02:0b.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

```

[COLOR="DarkRed"]acpi-support contents:
[/COLOR]```


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
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=false

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
#LOCK_SCREEN=true

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
ENABLE_LAPTOP_MODE=false
```

[COLOR="DarkRed"]and finally the xorg.conf file: [/COLOR]
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
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

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
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
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Anyone see anything in here that is an obvious issue?

- Ryan

---

### Post by Bluecircle on 2007-06-13
I assume you have tried sudo dpkg-reconfigure xserver-xorg? When you boot into recovery mode, what happens if you type "startx"? If you select Session -> Failsafe Terminal at the login screen can you get to the desktop?

---

### Post by rsain on 2007-06-14
I'm not at the machine right now - but will try this in a couple of hours. I believe I ran sudo dpkg-reconfigure xserver-xorg - after trying to install a ATI driver that didn't work.

I'm not sure what you mean by 'boot into recovery mode'... let me explain.

The install is on the machine, not a CD - so I'm actually getting into recovery mode from the Grub options (f6 - then choosing the recovery mode from there). I get no options for a "Session - Failsafe Terminal" - again I only have a command line. 

I'll report back when I get to that machine again.

Thanks for your help!

- Ryan

---

### Post by rsain on 2007-06-15
Ok,

Booted into recovery mode from the Grub options screen. 

Ran startx and, well, it produced the same thing. Just goes to black. I can tell that there is some sort of signal being sent to the monitor, because it is on and has a faint glow. But I have no desktop visible. 

go through sudo dpkg-reconfigure xserver-xorg again and see if I can get this set...

- Ryan

---

### Post by rsain on 2007-06-15
During the reconfigure I ran into an issue:

The first time I ran through the options I chose not to Autodetect my monitor. This allowed me to get through the entire reconfigure, but did not solve the problem.

This time I chose autodetect and, well, it did something I didn't expect. It went blank. 

The monitor is 13.3" and displays at 1280 x 800.

- Ryan

---

### Post by rsain on 2007-06-15
And I don't see where I can choose the Session -> Failsafe Terminal option. I just booted from the CD and on the install splashscreen I don't see anything of the sort.

- Ryan

---

### Post by rsain on 2007-06-19
bump.

---

### Post by Jimbo2184 on 2007-07-01
Hi.

Noticed something in your Xorg.conf file you posted earlier on. You're running an ATi Radeon Mobility 9600 M10 (RV350) card. I believe the correct driver to use is the radeon driver not the ati driver specified.

Try this:

```
sudo nano /etc/X11/xorg.conf
```

Edit this part of your Xorg.conf file:
Change:
```
Section "Device"
	Identifier	"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection
```

To this:

```
Section "Device"
	Identifier	"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection
```

Then issue:
```
sudo init 2
```
This will switch to Ubuntu's Runlevel 2 which loads X11, networking and system daemons for multi-user mode.

If you see the GDM logon prompt your graphics driver is working correctly. If nothing still appears can you attach your /var/log/Xorg.0.log file here as an attachment?

Hope this helps.

:)

---

