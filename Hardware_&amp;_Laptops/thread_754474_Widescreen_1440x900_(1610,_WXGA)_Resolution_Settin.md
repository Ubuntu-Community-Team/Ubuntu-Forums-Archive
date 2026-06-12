---
title: "Widescreen 1440x900 (16:10, WXGA) Resolution Setting Lost After Logging Out"
date: 2008-04-13
forum: Hardware &amp; Laptops
---

### Post by dragev.ca on 2008-04-13
I'm a new Linux user and am having problems using my widescreen monitor with its optimal native resolution, **1440x900** at **60 Hz** (aspect ratio - 16:10 or 8:5). After logging out of Ubuntu, the native resolution configured with the *Screen and Graphics Preferences* dialog is lost, and is set to 1280x768 (aspect ratio - 5:3). So, the boot splash screen and the log in screen are never displayed with the native resolution, and I have to reset the display resolution to 1440x900 every time I log in.

Operating Environment:
[INDENT]Desktop Computer: **HP Pavilion a730n**
Graphics Card: **Intel 915G**
```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
```
Monitor: **LG L194WTX** 19" widescreen LCD
OS: **Ubuntu 7.10** "Gutsy Gibbon" (fresh install)
[/INDENT]

Attempted Display Configuration Steps:
[LIST=1]
[*] Open *Screen and Graphics Preferences* dialog (*System* > *Administration* > *Screens and Graphics*)

[INDENT]Default Settings:
[INDENT]Screen tab:
[INDENT]Model: LCD Panel 1024x768
Resolution: 1280x768 at 60 Hz[/INDENT]
Graphics Card tab:
[INDENT]Graphics card (Intel 915)
Driver: intel - Experimental modesetting driver for ...[/INDENT][/INDENT][/INDENT]

[*] Change *Model* to "LCD Panel 1440x900 (widescreen)" (selected "Generic" > "LCD Panel 1440x900" from the list and checked off *Widescreen resolution*)
[*] Change *Resolution* to "1440x900" at "60 Hz"

[INDENT]After pressing *OK* a *displayconfig-gtk* message box appears with the instruction, "All users must log off for the changes to take effect".[/INDENT]

[*] Log Out / Log In (I'm the only logged in user)

[INDENT]Resolution is not correct :([/INDENT]

[*] Press the monitor's "auto image adjustment" hardware button

[INDENT]Message displayed by the monitor: "FOR OPTIMAL DISPLAY CHANGE RESOLUTION TO 1440x900"[/INDENT]

[*] Open *Screen and Graphics Preferences* dialog

[INDENT]Settings:
[INDENT]Model: LCD Panel 1440x900 (widescreen)
Resolution: 1280x768 at 60 Hz[/INDENT][/INDENT]

[*] Change *Resolution* from "1280x768" to "1440x900"

[INDENT]After pressing *OK* a *displayconfig-gtk* dialog appears with the question, "Do you want to keep the current configuration?". I press *Keep configuration*.

At this point there are unused pixels on the left side of the screen.[/INDENT]

[*] Press the monitor's "auto image adjustment" hardware button

[INDENT]No "change resolution" message appears this time. Resolution and pixel coverage is now perfect :)[/INDENT]

[*] Restart computer.

[INDENT]Same results as in steps #4-8 :([/INDENT]

[*] Repeated all previous steps again, except this time, I import the driver install file (l194wtx.inf) that came with the monitor on CD (import accomplished with *Add* from *Choose Screen* dialog), and then change *Model* (step #2) to "LG L194WTX(Analog) (widescreen)"

[INDENT]Same results as in steps #4-8 :([/INDENT]
[/LIST]

In summary, the problem is that I'm able to successfully set the optimal resolution, 1440x900, only after starting a new user session, but when I log out or restart system the setting is reverted to 1280x768. I also found that if I switch users, the other user has to configure the resolution also, but when switching back, the correct resolution set after logging in is maintained until I'm logged out.

All my configuration has been done through the GUI, and because I'm sure someone will be interested in seeing the **/etc/X11/xorg.conf** file, here are the sections that seem relevant to me (all the following was configured through the GUI; no manual edits):

```
Section "Device"
	Identifier	"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Boardname	"intel"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"LG"
	Modelname	"LG L194WTX(Analog)"
	Horizsync	28.0-83.0
	Vertrefresh	56.0-75.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1920	1200
		Modes		"1440x900@60"	"1600x1024@60"	"1440x900@75"	"1680x1050@60"	"1280x800@60"	"1680x1050@75"	"1280x768@75"	"1920x1200@60"	"1280x800@75"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
	EndSubSection
EndSection
```

---

