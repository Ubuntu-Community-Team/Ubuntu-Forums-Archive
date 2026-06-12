---
title: "Can't change resolution w/ Intel 915/910 Graphics Card"
date: 2007-02-06
forum: Hardware &amp; Laptops
---

### Post by mierow on 2007-02-06
I am new to Ubuntu and have searched this forum (and others) but so far all of the suggestions have not worked.  I'm am having an issue trying to change the resolution on my laptop.  Here is the card that I am using:

Mobile Intel® 915GM/GMS, 910GML Express Chipset Family 

I am also on a Lenovo ThinkPad R52, using Ubuntu 6.10

The only resolution that I am allowed to choose is 1024x768 (refresh rate:60Hz)

Yes - I have already installed "915resolution"
Yes - I have already edited "/etc/X11/xorg.conf" and added the resolutions of "1280x1024" and "800x600"

So far nothing has seemed to allow me to change the resolution.  I did some searching on Intel's site and found a Linux driver for this card [here]("http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1862&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21").  

Can anyone tell me:
1) Does this driver work to allow me to change resolutions?
2) If so, how do I properly install this driver?
3) Or is there something else I need to configure?

---

### Post by mierow on 2007-02-06
Also, here is my xorg.conf 

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"Option  "XAANoOffscreenPixmaps"
	BusID		"PCI:0:2:0"
	Option  	"XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
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
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

---

### Post by Surgeon General on 2007-02-06
> **mierow said:**
> I am new to Ubuntu and have searched this forum (and others) but so far all of the suggestions have not worked.  I'm am having an issue trying to change the resolution on my laptop.  Here is the card that I am using:

Mobile Intel® 915GM/GMS, 910GML Express Chipset Family 

I am also on a Lenovo ThinkPad R52, using Ubuntu 6.10

The only resolution that I am allowed to choose is 1024x768 (refresh rate:60Hz)

Yes - I have already installed "915resolution"
Yes - I have already edited "/etc/X11/xorg.conf" and added the resolutions of "1280x1024" and "800x600"

So far nothing has seemed to allow me to change the resolution.  I did some searching on Intel's site and found a Linux driver for this card [here]("http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1862&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21").  

Can anyone tell me:
1) Does this driver work to allow me to change resolutions?
2) If so, how do I properly install this driver?
3) Or is there something else I need to configure?

your best bet is to do a "sudo apt-get install 915resolution" from a terminal then run "sudo dpkg-reconfigure xserver-xorg". afterwards reboot and you'll be able to select the resolution you want.

hth.

---

### Post by mierow on 2007-02-07
Thanks.  That's the ticket.  After looking though a couple of other posts, I saw that I missed that step.  Thanks for the help.  Maybe you, or some here, can answer a related question.


Is it just me, or does the default font look goofy on a laptop?  Now that I've been able to play with the resolution (which is where I thought the problem was), I think the layout still looks weird.  I'm running a resolution of 1024x768 (max my laptop card will support).  I'm not sure if its the font or the size or what.  I've played with different fonts, changing the dpi, and anything else I can find.  Has anyone else seen this and be bothered by it, or am I just being picky?

---

### Post by Surgeon General on 2007-02-07
goofy? how's that? have you installed true type fonts (sorry can't recall the exact package name)?

---

### Post by MyR on 2007-02-08
I have the same grafics card, however my desired resolution is 1920x1200 (on edgy).
The default resolution was 1600x1200 (not even the proper ratio)

I have tryed 915resolution.
I also attempted to install the intel drivers. it failed & said something like i didnt have the latest kernel modules.
after running "sudo dpkg-reconfigure xserver-xorg" and rebooting, i am now using 1680x1050 (the proper ratio at least)
the 1920x1200 option is still unavailable.

my xorg.conf is nearly identical to the one above so i wont paste it. though it does have Modes "1920x1200" "1680x1050" "1440x900" "1280x800" "1024x768" "800x600" "640x480"

maybe ubuntu just wont support 1920x1200?? any ideas appreciated,

---

### Post by petrol on 2007-02-22
I ran the "sudo dpkg-reconfigure xserver-xorg" but I still do not have the selection when I go to System>Preferences>Screen Resolution. I have the intel card on an HP nc6220. If you have it working could you post your xorg.conf? Or do I need to change the resolution via another method? I am going to be running the 1680x1050 on a monitor attached to my docking station. Do I need to set the resolution back when detaching?
Here is my config:

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
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

Section "Device"
	Identifier	"Intel i915"
	Driver		"i810"
	BusID		"PCI:0:02:0"
	VideoRam	256000
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel i915"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by jis on 2007-02-22
I have Mobile Intel 910GML Express chipset in my laptop. If I start it with no external monitor attached, there is Default (1280x800) and 1024x768@60 visible in Xubuntu 6.10's Display Settings. If I attach a (Hitachi CM751ET) monitor and restart, only the external monitor is used, and there are different display modes available, namely Default (apparently the same), 1024x768@85, 800x600@85, and 640x480@85. All this happens with the same xorg.conf that has only "1280x800" in the Modes section. (I have not installed 915resolution, since I have no reason to belive that it works with the chipset of my laptop.)

---

### Post by jis on 2007-02-22
I have to add that returning from suspend state when the external screen is used returns to state where there is no proper display mode available. I have also tried hibernate earlier, but then I lost swap access and nowdays my PC seems to be very slow.

---

### Post by ramjet_1953 on 2007-02-23
Try this link.

[http://www.ubuntuforums.org/showthread.php?t=351647&highlight=915resolution](http://www.ubuntuforums.org/showthread.php?t=351647&highlight=915resolution)

Regards,
Roger :cool:

---

### Post by petrol on 2007-02-24
I had not tried those things but, they still did not work. I am starting to think that the universe doesn't want me to have a 22" wide screen. 

/etc/default/915resolution:

# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=30
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1680
YRESO=1050
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=32

sudo 915resolution -l:

Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

[COLOR="Red"]Mode 30 : 1680x1050, 32 bits/pixel[/COLOR]
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 1680x1050, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 1680x1050, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel


/etc/X11/xorg.conf:

Section "Device"
	Identifier	"Intel i915"
	Driver		"i810"
	BusID		"PCI:0:02:0"
	VideoRam	256000
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel i915"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


I tried booting with the monitor attached to my docking station. No Luck... Should I be changing the resolution in some other place than System>Preferences>Screen Resolution ?

:confused:

---

### Post by MyR on 2007-04-19
months later.. I *finally* got my resolution to 1920x1200 !!!
all i did was:
sudo 915resolution 3c 1920 1200 24
(my xorg.conf had previously been edited to contain the 1920x1200 modes)
then restarted x with ctrl+alt+backspace
and selected the correct resolution from system > preferences > screen res
I'm so happy!
also i learned that the changes made by 915resolution are transient (they go away after you reboot). i followed this how-to to add a script to allow the resolution at each boot. i have not yet tested it (i hate rebooting). [http://bonte.co.uk/myBlog/?p=97](http://bonte.co.uk/myBlog/?p=97)
peace

---

