---
title: "Getting the free radeon driver to work on my laptop."
date: 2007-02-05
forum: Hardware &amp; Laptops
---

### Post by jonaslehtonen on 2007-02-05
'ello.

Lacking 1280*800 resolution and decent acceleration on Dapper, I tried editing xorg.conf, replacing "vesa" with first "radeon", then "ati". On the first time (radeon) this caused a blank screen when booting up X, on the second (ati) it tells me that the X server crashed due to a lack of screen. 

Would someone help me fix this? I am fairly certain I'm committing some fundamental newbie mistake here, but I haven't yet found instructions on how to avoid said mistake.

For what that's worth, this is a Fujitsu Amilo 1437G laptop with an ATI Mobility Radeon x700. As far as I can tell it filled the requirements to use the free driver.

Thanks in advance.

---

### Post by Stemp on 2007-02-05
try to use the command :

```
sudo dpkg-reconfigure xserver-xorg
```

and set the video driver to ati or radeon (ati is a wrapper so it will use radeon in fact).

If it's not working look at the errors in the logs :

```
cat /var/log/Xorg.0.log | grep EE
```

---

### Post by jonaslehtonen on 2007-02-05
Thank you. Are there any files beside xorg.conf I need to back up in case of a mishap?

---

### Post by Stemp on 2007-02-05
To backup xorg.conf is enough and anyway you could run the reconfigure command again and set the driver to vesa ;)

---

### Post by jonaslehtonen on 2007-02-05
Okay. I tried setting it to ati (didn't find radeon on the list, tried to keep the other options at the same as best I could) which resulted in a crash for the X server. Here's the error you asked for: 

```
Current Operating System: Linux jonas-laptop 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

```

---

### Post by Stemp on 2007-02-07
These errors are related to a falsly detected wacom device, it's not a blocking error.
Are you sure it's the /var/log/Xorg.0.log file you have when your X is crashing ?
When X crash, hit ctrl+alt+f1, log in and type this command :

```
cat /var/log/Xorg.0.log | grep EE > xerror.txt
```

Then modify your X server (set it to vesa) and paste this file ;)

---

### Post by jonaslehtonen on 2007-02-07
I tried it a few times (commenting out the wacoms from my xorg.conf in one attempt), and it persists in giving me the same error file I just pasted. If this is of any importance, I notice that I have a refresh rate of 0 Hz only in the graphical resolution options. I'll post up the default and atified versions of the xorg.conf in a few hours once I get WLAN access on my laptop.

EDIT: Is it possible that the radeon driver is not installed at all? If so, where can I get it?

---

### Post by Stemp on 2007-02-07
> EDIT: Is it possible that the radeon driver is not installed at all? If so, where can I get it?

No it's part of the xserver-xorg-video-ati package.

For the wacom don't forget to comment the devices lines AND the Serverlayout or you will have some troubles.

---

### Post by jonaslehtonen on 2007-02-08
Sorry about the delay. Upon changing the driver to ati and commenting out the wacom parts, the following got pasted into the error log:

```
Current Operating System: Linux jonas-laptop 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) No devices detected.

```

---

### Post by Stemp on 2007-02-08
> (EE) No devices detected.

No devices detected ?? :( 

Please include the output of the **lspci** command.

---

### Post by jonaslehtonen on 2007-02-09
```
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:01:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
0000:01:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
0000:01:07.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
0000:03:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
```

Thar. Also, my xorg.conf at default settings:

```
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
	Option		"XkbLayout"	"fi"
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
	Identifier	"ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Driver		"vesa"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
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
EndSection

Section "DRI"
	Mode	0666
EndSection

```

((When changing to ati driver I changed vesa to ati and commented out all sections that had anything to do with wacom, including the last three lines of ServerLayout))

---

### Post by Stemp on 2007-02-09
Well it seems to be a bug in xserver see : [Bug #22985]("https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/22985")

The workaround : [EdgyKnownIssues/22985]("https://wiki.ubuntu.com/EdgyKnownIssues/22985")

Hope it will work for you ;)

---

### Post by jonaslehtonen on 2007-02-09
Ach, no such luck. The X server still crashes due to lack of screen. I put in the extra line in my xorg.conf but that did not appear to make it work (I assumed that the kernel options are specifically related to booting from the CD and not necessary here).

Thank you for the help, at any rate (assuming there are no other tricks left to try for now?). I'll play around with it some more later on, perhaps upgrade to Edgy, or I could just wait 'til Feisty and its eyecandyboosters come along :)

---

### Post by Stemp on 2007-02-10
Well well well..... I looked for your laptop in [TuxMobil]("http://tuxmobil.org/mylaptops.html") and they are all using the fglrx driver.

[http://www.martinhenze.de/2006/01/03/ubuntu-linux-on-fujitsu-siemens-amilo-m1437g](http://www.martinhenze.de/2006/01/03/ubuntu-linux-on-fujitsu-siemens-amilo-m1437g)
[http://ubuntu.hu/index.php?title=FSC_Amilo_M1437G_laptop_be%C3%A1ll%C3%ADt%C3%A1sa](http://ubuntu.hu/index.php?title=FSC_Amilo_M1437G_laptop_be%C3%A1ll%C3%ADt%C3%A1sa)

I guess you have to try to install the proprietary driver : 

```
sudo aptitude install xorg-driver-fglrx fglrx-control libqt3-mt   

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

---

