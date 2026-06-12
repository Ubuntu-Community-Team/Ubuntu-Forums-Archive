---
title: "Motion M1400/7.10 Experience"
date: 2008-01-27
forum: Hardware &amp; Laptops
---

### Post by pingnak on 2008-01-27
This is what I went through to get my trusty, rusty little Motion M1400 to run Ubuntu.

Plug in external CD drive and boot up the 7.10 ISO I burned.

Booted fine after navigating with joypad and pressing middle button.

Observe Stylus doesn't work.  Sound doesn't work, either.

Bluetooth Keyboard & Mouse I had just used wouldn't work, either.  No BT icon.

Plugged in a USB hub and hardwire USB mouse/keyboard.  Felt less like a dork.

Turned computer over awkwardly on its USB cables; the screen flipping button doesn't work.

Got it connected to my wireless network without any fuss.

Looked up "Motion M1400 Linux Howto"

Found [http://gentoo-wiki.com/HARDWARE_Motion_Computing_M1400](http://gentoo-wiki.com/HARDWARE_Motion_Computing_M1400)  and it looks promising.

Test sound with an MP3 off the Windows drive.  Mounted and found, no problem.

Added MP3 CODEC to default player... aww shucks, no sound, but no error, either.

Tinkered with System->Preferences->Sound to no avail.  Oh well, will try later.

Repartitioned drive to make a place to setup Ubuntu 7.10

Had to go back and 'delete' the unformatted partition I made for the installation because it made the CD boot crash on a blank screen.  I didn't see any error messages, but it would just get most of the way through with booting and then reboot.

Got it installed. 

Wireless network worked immediately.  Patched it all up current.

Bluetooth icon isn't there, and should be.  Researched a bit, looks like there is no bluetooth driver for the Widcomm device, period.

Followed the X11 directions not involving recompiling/patching things on [http://gentoo-wiki.com/HARDWARE_Motion_Computing_M1400](http://gentoo-wiki.com/HARDWARE_Motion_Computing_M1400) to configure tablet pointer.  Restarted and worked.  No 'right click' at the moment.  This thread has some useful crumbs, too... [http://ubuntuforums.org/showthread.php?t=63186](http://ubuntuforums.org/showthread.php?t=63186)

Sound wasn't working, but did work when I plugged headphones in.  Needed to be set up with the OSS mixer (ALSA mixer didn't work at all).  Had to enable all the audio settings and peck through the sliders and checkboxes.  'External Amp' needs to be cleared, like the one article said.  Unmuted everything until I heard sound, tweaked around a bit, then went back through and re-muted things until I had relatively few things 'on' to tinker with, but control for what I needed.

sudo apt-get install wacom-tools

OK, rotating the X display with 'xrandr -o' like the article says just locks it.  A bug?  Sure behaves like a bug.  The mouse respond to things, but clicking, typing, etc. goes nowhere.  Sigh.  Control-Alt-Backspace.  Not very useful, all in all.

Added the extra parameters in TabletGuy's post on the second page of [http://ubuntuforums.org/showthread.php?t=63186](http://ubuntuforums.org/showthread.php?t=63186) to enable the 'right-click'.  Control-Alt-Backspace and I have right-clicks with the pen.

Discovered 'onboard' 0.87 was already installed in Ubuntu via (System->Administration->Synaptic Package Manager) after going to all the trouble of tracking it down and discovering it didn't have an installer that I could manually invoke.  Made a little panel launcher icon in Gnome for it and picked a keyboard-looking icon for it.
[https://launchpad.net/onboard](https://launchpad.net/onboard)

OK, so I have video, audio, tablet pen, wireless/lan

No bluetooth, and the 'brightness' Panel widget doesn't work.  I don't know if this is just because I have the glass 'see outside' version of the panel or not.

Drat.  I guess I'll have to swap the wired glow-in-the dark keyboard and mouse and use the bluetooth ones with my honkin' big notebook.

After some tinkering with the 'brightness', this worked for me.  Initially it wouldn't even let me change the value as 'root', so I changed its permissions and then suddenly it worked just fine.  What I also discovered was that the 'brightness' settings are far from standard; after /proc/acpi/video, it's anybody's guess where 'brightness' will be in that tree.  It was different for my tablet from the 'HOWTO' article, and it was different on my other notebook when I looked.

sudo chmod 666 /proc/acpi/video/GFX0/LCD/brightness

Then a shell script I named 'dim'... takes 0..15 as setting; 'dim 15' for brightest.
#!/bin/bash
	echo $1 > /proc/acpi/video/GFX0/LCD/brightness

I'm sure that allowing anybody to touch 'brightness' is a security issue of sorts, but I'd rather be able to use the tablet on battery for six hours than two, and it looks like it rejects 'bad' values pretty reliably.

Then I rebooted to check it would still boot windows, and there was the small matter of GRUB not having my Windoze partition in the list.  With a small, sick feeling in my stomach I checked and the Windows partition was still there.  It was.  I had a drive image backup of it, so no BIG loss if it got clobbered.  So I got to edit /boot/grub/menu.lst to add it.  After a little searching around on the web, it turns out for whatever reason, even though the space I made had the Linux partition physically first, the Windows id was '0,0'.  Okie dokie.  I booted Windows and 'all was well', then booted back to Linux again.  
```

title         Windoze
root          (hd0,0)
chainloader   +1

```

At this point I more or less got busy installing apps with no further significant problems.  I can live without the bluetooth doohicky, I suppose.  

Oh, I guess the little retarded thumb scanner doesn't work, either, but I never used it anyway.  I'd rather peck passwords in with a stylus than let some bit of software 'promise' to keep them safe for me.  I don't let the browser remember any, either.

This is what 'xorg.conf' ended up looking like with the tablet pen all configured...
```

# xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option 		"Button2" 	"3"	# Add pen 'right-click'
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
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
 	InputDevice "stylus" "SendCoreEvents"
   	InputDevice "cursor" "SendCoreEvents"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

# Here we define the Tablet/Pen devices, you need to
# "emerge linuxwacom" to add the appropriate driver
# ("wacom") to your system.
# The tablet is connected via an internal serial port
# which needs to be initialized with setserial at
# boot time.
# Please "emerge setserial" and add the following line
# to /etc/serial.conf:
# /dev/ttyS0 port 0x0238 irq 4 autoconfig
Section "InputDevice"
   Identifier "stylus"
   Driver     "wacom"
   Option     "Device"        "/dev/ttyS0"
   Option      "Type"          "stylus"
   Option      "ForceDevice"   "ISDV4"
   Option     "SendCoreEvents"
EndSection

Section "InputDevice"
   Identifier "cursor"
   Driver     "wacom"
   Option     "Device"        "/dev/ttyS0"
   Option     "Type"          "cursor"
   Option     "ForceDevice"   "ISDV4"
   Option     "SendCoreEvents"
EndSection


```

lspci sez...
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
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
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)

lsusb sez...
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 08ff:2500 AuthenTec, Inc. *(Probably that thumb doohicky)*
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

Added...
Buttons do work:
The dpad works as arrows and enter.
The triangle button launches firefox.
The others don't seem to have an obvious effect, including the inset one.

Added this tip...
OK, the first time I grabbed it to surf the web with the pen and without the keyboard and mouse, I had to plug in a keyboard long enough to log in with my password and then figure out how to enable 'automatic login' () , because there was just no way to initially enter my password.  After that, it still insists on prompting for my 'keyring password' anyway because something internally isn't passing it along like during the 'normal' login.  

To do this, System->Administration->Login Window, Security Tab, Check 'Enable Automatic Login' and pick your user account, then restart to test, or your tablet will remain tethered to a keyboard.  Mind the physical security of your tablet, as any PC, because anybody can still make it boot off external media and readily access your files, even if you have a login password.  Even setting a BIOS level password to protect against booting is no assurance, as resetting it is relatively easy on most computers, and if not it's just as easy to pull the drive, mount it with another computer and put it back.

I'm also shopping for a little Linux compatible Bluetooth USB thumb because I bought my bluetooth keyboard and mouse for the tablet.  It's annoying, but a $20 adapter is still a lot less bother than the USB hub and wires, and infinitely less bother than grabbing the Bluez source, reverse engineering the built-in Widcomm BT device and spinning my own driver.  A bit too much of a side-trip for me, I'm afraid.  Looks like the winner might be  'D-Link DBT-120' for being the smallest one that has Linux support.

Also the privileges on the 'brightness' file reset (annoyingly) after I rebooted.  Looks like I'll have to peck in my password to change the brightness...
#!/bin/bash
# My 'dim' script...
	sudo chmod 666 /proc/acpi/video/GFX0/LCD/brightness
	echo $1 > /proc/acpi/video/GFX0/LCD/brightness

After all of that, I managed to enjoy some web surfing without too much additional bother before I fell asleep.

---

### Post by pingnak on 2008-02-01
Another tidbit: The 'grub' menu is inaccessible by default.  I can't press 'escape' until a keyboard is plugged in.  Sorted out by editing menu.lst and commenting out 'hiddenmenu'.

The Bluetooth USB dongle I settled for was the Cirago BTA 3210.  It sticks out about 5mm from the USB port, which is just far enough that Motion's rubber grippy condom thing bows out.  I might just cut a hole in it over the slot with the bluetooth adapter in it, and Ubuntu spotted it instantly.  From there it was just 'right-click' on the bluetooth icon and pick the Services tab in preferences, then add my keyboard and mouse.

---

### Post by trinitrotoluene on 2008-05-09
Here are my experiences:
[http://forums.murc.ws/showthread.php?p=651271#post651271](http://forums.murc.ws/showthread.php?p=651271#post651271)

I just upgraded to 8.04 and that was a bad idea.  Several things aren't working:

* onBoard seg faults ([http://ubuntuforums.org/showthread.php?t=769521&highlight=m1400](http://ubuntuforums.org/showthread.php?t=769521&highlight=m1400))
** Update: [https://bugs.launchpad.net/ubuntu/+source/virtkey/+bug/220475](https://bugs.launchpad.net/ubuntu/+source/virtkey/+bug/220475)
** Update: Update includes a fix to virtkey which makes onBoard useable
* The stylus stopped working
** Update I had to change my xorg.conf to use **/dev/input/wacom** instead of */dev/wacom*
* Battery monitor doesn't work
** acpi reports the wrong percentage -- for me it's stuck at 35% tho my laptop has been plugged in all night.
** After testing standby mode, acpi started reporting what appears to be a correct charge
*** Restarted and back to having an incorrect percentage

---

