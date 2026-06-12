---
title: "samsung syncmaster 205BW on a laptop screen resolution"
date: 2006-12-17
forum: Hardware &amp; Laptops
---

### Post by waldorf on 2006-12-17
I just got a Samsung SyncMaster 205BW and I want to use it with my laptop (HP Pavilion dv4000).

Not sure how to get the resolution correct (1680x1050 I believe).

Any suggested how to's out there?

Thanks in advance!

---

### Post by waldorf on 2006-12-18
bump. Help please!

---

### Post by javierfh on 2006-12-18
> **waldorf said:**
> I just got a Samsung SyncMaster 205BW and I want to use it with my laptop (HP Pavilion dv4000).

Not sure how to get the resolution correct (1680x1050 I believe).

Any suggested how to's out there?

Thanks in advance!

Hi,

i have same monitor as you have and no problem to get such resolution.
Are you using the correct drivers for your video card?
Have you checked that you have the correct values in Xorg.conf?

Just my two cents.

Javi

---

### Post by waldorf on 2006-12-18
Thanks Javi!

xorg.conf is as follows (note that I did add in 1680x1050 but it didn't work so I took it out):

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
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
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
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

---

### Post by javierfh on 2006-12-18
Hi,

really cant say much but there is something i cant see there, have you tried to add your refresh rates? everything else seems correct for me.
If that doesnt work, I suggest to try to find the newest drivers for your video card and well the resolution should be fine.

I dont know if that will help, but just in case here you have my xorg.conf

Please let me know if you manage to make it work, im curious :D


Javi

 
> 

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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fi"
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

Section "Device"
	Identifier	"NVIDIA GeForce 6600GT"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
EndSection

Section "Monitor"
	Identifier	"Samsung SyncMaster 205 BW"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce 6600GT"
	Monitor		"Samsung SyncMaster 205 BW"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection



---

### Post by waldorf on 2006-12-18
Javi,

Thanks its definitely better. I made it to 1600x1200 but its not quite right. Its supposed to be 1680x1050. Any thoughts?

Thanks again!!!!

xorg.conf is now

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
#	Identifier	"Generic Monitor"
	Identifier 	"Samsung SyncMaster 205 BW"
	Option		"DPMS"
	HorizSync 30-81
	VertRefresh 56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
#	Monitor		"Generic Monitor"
	Monitor		"Samsung SyncMaster 205 BW"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1600x1200" "1440x900" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1600x1200" "1440x900" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1600x1200" "1440x900" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1600x1200" "1440x900" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1600x1200" "1440x900" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1600x1200" "1440x900" "1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"

---

### Post by waldorf on 2006-12-18
One other thought:

from /var/log/Xorg.0.log

(II) I810(0): Samsung SyncMaster 205 BW: Using hsync range of 30.00-81.00 kHz
(II) I810(0): Samsung SyncMaster 205 BW: Using vrefresh range of 56.00-75.00 Hz
(II) I810(0): Not using mode "1680x1050" (no mode of this name)
(II) I810(0): Increasing the scanline pitch to allow tiling mode (1600 -> 2048).
(--) I810(0): Virtual size is 1600x1200 (pitch 2048)

---

### Post by javierfh on 2006-12-19
> **waldorf said:**
> One other thought:

from /var/log/Xorg.0.log

(II) I810(0): Samsung SyncMaster 205 BW: Using hsync range of 30.00-81.00 kHz
(II) I810(0): Samsung SyncMaster 205 BW: Using vrefresh range of 56.00-75.00 Hz
(II) I810(0): Not using mode "1680x1050" (no mode of this name)
(II) I810(0): Increasing the scanline pitch to allow tiling mode (1600 -> 2048).
(--) I810(0): Virtual size is 1600x1200 (pitch 2048)


Hello,

nice to see that you made some progress following my instructions :D to be honest im quite new in linux, using it since may, so im still learning, but glad that i can help even if it is little bit.

So, if i understood right, linux tries to set the best resolution from the list of resolutions you put there. So if you would remove the two with 1680 and 1600, it will try with the next.

In your case the 1600x1200 seems to be possible resolution, but the 1680x1050 its a wrong one or not possible.

So only thing that comes to my mind is that, if you copied the right refresh values from my xorg.conf (i took them from specs of the monitor) and then the right resolution lists, the problem comes from your video card. 
As i said try to look in the forums for problems with your video card, and maybe try to check if that one supports the widescreen format. If i remember right some friend once told me about some old cards not supporting widescreen mode...that might be the reason.

Please keep me informed, im curious :D and well i will try also to see if i can find some hint, its a matter of pride, first time i can help someone :D

Javi

---

### Post by javierfh on 2006-12-19
Another interesting thing from your xorg.conf is that seems that according to your xorg.conf the system detects that you have 
> 
Device "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"


but then where you have the driver it shows

> 
Driver "i810"


maybe you want to make sure that you use the latest and right driver, just in case.
Im not sure but that one sounds like inter 800 series..and you seem to have 900 series.

I checked also specs of your laptop and it seems they come with i900 series cards.

Javi


P.S. in intel site they have drivers download page for linux  [http://downloadfinder.intel.com/scripts-df-external/Product_Filter.aspx?ProductID=1862&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Product_Filter.aspx?ProductID=1862&lang=eng)

---

### Post by javierfh on 2006-12-19
And you might want to take a look to that thread, specially the last post 

[http://www.ubuntuforums.org/showthread.php?t=67165&highlight=i915](http://www.ubuntuforums.org/showthread.php?t=67165&highlight=i915)

Please let me know if you manage to solve it.

Javi

---

### Post by eXisor on 2006-12-19
You probably need to specify the modelines the monitor supports.

See my post here... [http://ubuntuforums.org/showpost.php?p=1905799&postcount=2](http://ubuntuforums.org/showpost.php?p=1905799&postcount=2) to see how.

---

### Post by waldorf on 2006-12-19
Javi and eXisor,

Thank you both very much for reponding to my pleas!

Its a long story but I suddenly find myself without the monitor for a week, so it looks like I will need to shelve this project for the week.

But I am sure to get back to it and both of you in a week.

Thanks again!

---

### Post by javierfh on 2006-12-20
> **waldorf said:**
> Javi and eXisor,

Thank you both very much for reponding to my pleas!

Its a long story but I suddenly find myself without the monitor for a week, so it looks like I will need to shelve this project for the week.

But I am sure to get back to it and both of you in a week.

Thanks again!

By the way, 

all i know about resolution, which is not much, i have learned when fighting to have the twin view working. I wanted to have two screens working and it was nice.
So if you are interested about that, im sure you can also do it since you have the screen of the laptop plus the monitor :D
Might be that you dont need it, nor like it...but well just in case, you can search some of my old posts, i was getting very nice help about it.

Feel free to bother me as much as need it..and i hope you make it work

So merry xmas and hehe good luck with the project next week :D


Javi

---

### Post by waldorf on 2006-12-26
I'm back and even with the advice from both of you still no go.

Couple of questions.

If this is a driver problem, how do I install the driver once I download the tar.gz?

This is what xorg.conf looks like and the result is that I can get 1600x1200 but it won't all fit on the screen or I get 1280x1024 and it fits but obviously its not right.

Thanks!!!

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
	Option		"SHMConfig"		"true"
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
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
#	Identifier 	"Samsung SyncMaster 205 BW"
	Option		"DPMS"
	HorizSync 	30-81
	VertRefresh 	56-75
	# 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
  	Modeline "1680x1050_60"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
  	# 1600x1200 @ 85.00 Hz (GTF) hsync: 107.10 kHz; pclk: 234.76 MHz
  	Modeline "1600x1200_85"  234.76  1600 1720 1896 2192  1200 1201 1204 1260  -HSync +Vsync

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
#	Monitor		"Samsung SyncMaster 205 BW"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1680x1050_60" "1600x1200_85"
#"1600x1200" "1440x900" "1280x800"
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

### Post by waldorf on 2006-12-26
Is it possible that Intel 915 graphics card does not support 1680x1050? If so is this a lost cause?

---

### Post by waldorf on 2006-12-30
I give up. I tried so many different suggestions on different posts and I just could not get it to work.

---

### Post by peacekpr on 2007-01-13
I am having some trouble with getting this monitor to work how I would like it to.  Basically, I want the Syncmaster 205BW to be the secondary monitor on my laptop (and the laptop's LCD to be the primary, obviously).  Microsoft Windows has the capability to autodetect an external monitor and use it according to the installed drivers, but I have not yet seen this functionality in Linux - and I *really* need it.  So I would like my external Syncmaster 205BW to be autodetected by the X Server when plugged in (not necessary hot-plug) and my desktop displayed according to certain settings I have presumably specified in xorg.conf.  

_Relevant System Information:_
[LIST]
[*]Distribution: Ubuntu Edgy Eft 6.10 for AMD64
[*]Video Adapter: ATI Radeon Xpress 200
[*]Video Driver: ATI Binary Driver v8.32.5
[*]External Monitor: Syncmaster 205BW
[/LIST]

If anyone knows of a way for the X Server to autodetect an external monitor and apply specified settings, let me know.  I am very interested in finding out how to do it.

---

### Post by RobotEv il on 2007-02-22
> **waldorf said:**
> I give up. I tried so many different suggestions on different posts and I just could not get it to work.


HI

Did you actually find a solution to this problem?  if not i had a similar issue with my laptop and it required a resolution of 1280x900, it uses the same chipset you have.  
I solved the problem with a nice program called 915resolution, i believe there is also an 855resolution that can do the trick as well if 915 doesnt work for you.

I also had to state i was using the 800series chip in xorg.conf even though i actually had the 900

heres a link
[http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)   which seems to have exceeded its bandwidth for the moment
[http://packages.debian.org/unstable/x11/915resolution](http://packages.debian.org/unstable/x11/915resolution)   this is a debian package, not sure how well it will work on ubuntu.

Hope this helped

Also im new to this forum and registered simply because i had endless problems trying to get this to work, im more of a slackware fan but hey linux is linux and helping is helping

RobotEvil

---

### Post by peacekpr on 2007-03-17
This seems like the best thread to post my solution to getting my Samsung SyncMaster 205BW to work as a second (cloned) monitor on my laptop's external VGA port.  In order to get the monitor to work properly, I had to put the following information in my "Device" section in xorg.conf.  But first a couple of comments:[LIST]
[*]I am running X Window System Version 7.1.1 on 2.6.17-generic x84_64.
[*]Video driver:  fglrx 8.32.5
[*]Video hardware:  ATI Radeon Xpress 200M (integrated)
[*]The "MergedFB" option may not be necessary.  Xorg.0.log states it isn't used, but it also says that about the "ForceMonitor" option (which was necessary to get the monitor to work).  So take Xorg's warning about "MergedFB" with a grain of salt. ;-)
[*]My laptop display is in "virtual" mode meaning you have to pan around the screen to get where you need to go on the desktop.  I haven't attempted to figure out how to get rid of this issue as I really don't care since my laptop lid stays closed when I am using the external monitor.  When the external monitor is not in use, the laptop display's resolution is correct.
[*]Upon restarting Xorg with the external monitor connected, I had to hit the "Auto" button on the monitor itself (so that it could synchronize the signal?).
[*]3D software (such as Beryl and Google Earth) work smoothly on the external display.
[*] For my configuration, my machine (perhaps Xorg?) will lock up when I log out of Gnome at which time I must reboot.  I can avoid this by just restarting Xorg without properly logging out.  I'm not too fond of that since my desktop settings and window information from that Gnome sesion are not saved, but hopefully I'll be able to figure it out.  I'm not sure why this is happening, but it's my only gripe.[/LIST]```

Option "MergedFB" "true" #I'm not sure if this is really doing anything at this point.
Option "ForceMonitor" "lvds,crt1" #LVDS is the laptop LCD
Option "HSync2" "30-81" #Reference Samsung technical specifications
Option "VRefresh2" 56-75" #Reference Samsung technical specifications
Option "OverlayOnCRT2" "true"
Option "Mode2" "1680x1050" #Reference Samsung technical specifications

```Good luck,
Jason

---

