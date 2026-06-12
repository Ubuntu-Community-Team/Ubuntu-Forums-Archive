---
title: "Fixed it: Resolutions higher than 1600x1200 on a CRT"
date: 2009-02-23
forum: Hardware
---

### Post by Asmyldof on 2009-02-23
Hello friendly people of the Ubuntu forums!

I have been trolling your archives for two days, googling my pants, shirt and socks off, but I managed it (see attachment and/or code below).

Using information provided here, my own knowledge on VGA and DVI signals and using the [Modeline how-to pages](http://howto-pages.org/ModeLines/) to find out what those numbers mean I made a xorg.conf enumerating the modes my HP P1230 supports (seeing it has a bandwidth limit of 395MHz, that's a lot!). There are still bugs, because my ATI driver now detects it as having a maximum of 4096x4096, but all the modes listed (up to 1920x1440 @ 90Hz) are supported as far as I could test. I'd love to also have the 2048x1536 @85Hz it supports, but for now...

I'm not sure if I will keep working on this, as my fav. 1880x1400 @ 70Hz mode is included (my cables aren't up to the 90Hz alternative without pixelbleed :'(, never knew as M$ W1nXP doesn't support it!)

Note to non-P1230 users gazing upon this, the scan pulse positions in these modelines are based on standard 15% to 20% and 20% to 30% of the overflow (amount of clocks between Hdisp/Vdisp and Htotal/Vtotal). This works fine for electronic scan monitors such as this CRT (because they automatically compensate the timing to fit the signal on the glass), but other types may not display everything on your screen. I refer you to the modeline howto pages as linked above to try and fix that.

I hereby provide you all with my work (xorg.conf) - No need to copy-paste, just download the attached txt file:
```

# Code By: Robert van Leeuwen
# very loosely based on DebConf's basic xorg.conf
# contact: ubuntu@asmyldof.com
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "Screen[0]" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Modes"
# HP P1230 Factory presets:
	Identifier     "Modes[0]"
	ModeLine     "640x480" 25.2 640 665 708 800 480 481 485 525 # Preset #1
	ModeLine     "640x480" 36.0 640 670 721 831 480 481 484 509 # Preset #2
	ModeLine     "720x400" 28.3 720 748 796 898 400 401 405 450 # Preset #3
	ModeLine     "800x600" 49.5 800 840 908 1055 600 601 603 625 # Preset #4
	ModeLine     "800x600" 56.3 800 839 905 1048 600 601 604 632 # Preset #5
	ModeLine     "1024x768" 65.0 1024 1033 1048 1083 768 769 772 800 # Preset #6
	ModeLine     "1024x768" 94.5 1024 1080 1174 1375 768 769 772 808 # Preset #7
	ModeLine     "1152x870" 100.0 1152 1200 1281 1455 870 871 875 916 # Preset #8
	ModeLine     "1280x1024" 108.0 1280 1345 1454 1687 1024 1025 1028 1066 # Preset #9
	ModeLine     "1280x1024" 135.0 1280 1345 1454 1687 1024 1025 1028 1066 # Preset #10
	ModeLine     "1280x1024" 157.5 1280 1351 1471 1726 1024 1025 1029 1073 # Preset #11
	ModeLine     "1600x1200" 202.5 1600 1689 1839 2158 1200 1202 1206 1251 # Preset #12
	ModeLine     "1600x1200" 229.5 1600 1689 1839 2158 1200 1202 1206 1251 # Preset #13
	ModeLine     "1792x1344" 204.8 1792 1897 2074 2449 1344 1345 1349 1393 # Preset #14
	ModeLine     "1792x1344" 261.0 1792 1898 2077 2455 1344 1346 1352 1417 # Preset #15
	ModeLine     "1920x1440" 234.0 1920 2028 2211 2600 1440 1442 1447 1500 # Preset #16
	ModeLine     "1920x1440" 297.0 1920 2001 2138 2428 1440 1444 1458 1630 # Preset #17
	ModeLine     "2048x1536" 388.0 2048 2173 2384 2832 1536 1538 1544 1611 # Preset #18
# Additional, community inspired resolutions:
	ModeLine     "640x480" 73.9 640 675 735 864 480 482 486 534
	ModeLine     "768x576" 108.3 768 768 768 1056 576 578 583 640
	ModeLine     "800x600" 38.2 800 800 800 1024 600 601 603 622
	ModeLine     "800x600" 118.0 800 800 800 1104 600 602 607 668
	ModeLine     "1024x768" 185.6 1024 1024 1024 1424 768 770 776 841
	ModeLine     "1280x768" 231.5 1280 1280 1280 1776 768 770 776 840
	ModeLine     "1600x1200" 289.2 1600 1600 1600 2154 1200 1203 1213 1342
	ModeLine     "1880x1400" 258.2 1880 1880 1880 2519 1400 1404 1417 1576
	ModeLine     "1880x1400" 298.0 1880 1880 1880 2519 1400 1404 1417 1577
	ModeLine     "1880x1400" 337.8 1880 1880 1880 2519 1400 1404 1417 1577
EndSection

Section "Monitor"
	Identifier   "Monitor[0]"
	VendorName   "HP"
	ModelName    "Dell/HP P1230 Diamontron"
	UseModes     "Modes[0]"
	HorizSync    30.0 - 140.0
	VertRefresh  50.0 - 160.0
EndSection

Section "Device"
	Identifier  "Device[0]"
	Driver      "fglrx"
	BoardName   "Radeon HD3870 PCIE Dual DVI"
	Option	    "DesktopSetup" "clone"
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "Screen[0]"
	Device     "Device[0]"
	Monitor    "Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Depth     15
		Modes    "2048x1536" "1920x1440" "1880x1400" "1792x1344" "1600x1200" "1280x1024" "1280x768" "1152x870" "1024x768" "800x600" "768x576" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "2048x1536" "1920x1440" "1880x1400" "1792x1344" "1600x1200" "1280x1024" "1280x768" "1152x870" "1024x768" "800x600" "768x576" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "2048x1536" "1920x1440" "1880x1400" "1792x1344" "1600x1200" "1280x1024" "1280x768" "1152x870" "1024x768" "800x600" "768x576" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "2048x1536" "1920x1440" "1880x1400" "1792x1344" "1600x1200" "1280x1024" "1280x768" "1152x870" "1024x768" "800x600" "768x576" "720x400" "640x480"
	EndSubSection
EndSection

```

after making these changes I just ran:
```

aticonfig --initial

```
(after getting the latest driver from ati.amd.com of course)

---

