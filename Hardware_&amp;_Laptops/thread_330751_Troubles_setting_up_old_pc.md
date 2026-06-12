---
title: "Troubles setting up old pc"
date: 2007-01-03
forum: Hardware &amp; Laptops
---

### Post by heartwort on 2007-01-03
Hi there!

I've setting up Ubuntu 6.06 to run on an old pc and have run into several problems.

My system thus far:

Old motherboard ? early-mid 90s but seems to handle everything so far
360 MB RAM
new 160 GB EIDE Hard drive (put in BIOS as a smaller hd in order to be recognized, /boot mounted in small partition so BIOS can find it, no other OS)
floppy drive that came with it originally - not working
cd-rw - worked without problem
ethernet - worked without problem
old Soundblaster card - model CT4180 - no sound
old Matrox vga monitor - can't change resolution

Problems and what I've done thus far garnering info from online:

_Floppy drive won't mount_ - 

floppy icon shows up under Computer - tried to right click and mount there and got message:  

Unable to mount selected floppy drive;   mount: mount point /media/floppy0 does not exist

I added the last line to my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hda5       /home           ext3    defaults        0       2
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0 	/media/floppy0  vfat rw,user,noauto 	
0 	0

I checked Users and Groups.  Ben (the only user account) and haldaemon are the only users listed.

I don't know where to go from here on this matter.  

When I typed "sudo gedit /etc/fstab" in my terminal to edit fstab I also got:

ben@ben-desktop:~$ sudo gedit /etc/fstab
Password:
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
ben@ben-desktop:~$



Which I believe leads me to Problem 2:

_No Sound_

When trying to play a ogg file from Examples I get:

Totem could not start up.  Could not establish connection to sound server.

When I click on the volume control icon I get:

No volume control gstreamer plugins or devices found.

In the Synaptic Package Manager I show gstreamer0.10-alsa, -plugins-base, and -plugins-base-apps are all installed as well -plugins-good and -plugins-ugly, but not plugins-bad.

Alsa-base and alsa-firmware-loaders is also installed.

What else to try?


Problem 3:

_Monitor Resolution_

It's an old monitor and running under a screen resolution of 640x480 a lot of my screen becomes cut off.  When I ran Win98SE I had the resolution set at 800x600 and very little if anything was cut off.  Under System>Preferences>Screen Resolution I am only given the choice of 640x480.  I've read that all the options listed in /etc/X11/xorg.conf would show up there but that doesn't seem to be the case.  Here's the file:



Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
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
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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

Section "Device"
	Identifier	"Matrox Graphics, Inc. MGA 2164W [Millennium II] AGP"
	Driver		"mga"
	BusID		"PCI:1:0:0"
	Option		"OldDmaInit"		"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Matrox Graphics, Inc. MGA 2164W [Millennium II] AGP"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Any other fixes for an old monitor out there?





I'm something of a Linux novice so please leave me details with your suggestions so I can try them.  Thanks!

Heart

---

### Post by az on 2007-01-03
Floppy:  Make sure it is enabled in BIOS.  Make sure it is properly connected and that you have not flipped the connector around (unlid ide har drives, you can plug it in both ways).

Since floppies are not hotpluggable (when you insert a floppy) there is an entry for a floppy drive in your fstab even if it was not there.

Sound:  See here:
[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)

Resolution:

Boot into recovery mode and run

dpkg-reconfigure xserver-xorg

Pick the default for everything except color depth.  Pick 15-bit.  Your card does not have enough ram to support higher color depths at more than 800x600.

---

### Post by heartwort on 2007-01-04
Thanks, azz.

The 15-bit color depth seemed to do the trick although reconfiguring xserver-xorg was kind of scary.  I ended up multiple barely visible ubuntus and a bunch of error messages I have no idea about.  I went back to Recovery and edited my xorg.conf file back to the way it was except for the color depth.  

Floppy:

It's all set in the BIOS.  I tried switching the cable - not sure - the light is no longer on but then it was on ALL the time before.  There was no line for the floppy in fstab before I edited it but apparently I had too many spaces or something.  Booting in Recovery mode I saw the warning that there was a bad line in fstab and went in and fixed that.  However, I still get:

Unable to mount selected floppy drive; mount: mount point /media/floppy0 does not exist


I'll check the link out for sound.  I'm out of time today.


Thanks!

Heart

---

