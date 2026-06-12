---
title: "Monitor refresh rate"
date: 2005-06-10
forum: Hardware &amp; Laptops
---

### Post by mentalinc on 2005-06-10
Ok this is my first post so therefore i am a complete noob

now onto business:

i have an AOC 7klr [Link to HTML Manual](http://64.233.179.104/search?q=cache:RiXZIe2uinMJ:www.aocmonitor.com/support/manuals/7KLR.pdf+aoc+7klr&hl=en&client=firefox) 

i run in windows xp with no problems 1024 *768 at 100 refresh rate.

however when i run in Hoary i can only get 85 when i put the info from the manual site into the hor and vert -

this is bad as my eyes hurt real bad after using the computer for a few hours - yet the monitor is fine to look at in windows xp forever.

i have added under 
Section "Monitor"
Modeline "1024x768@100" 126.64 1024 1056 1536 1568 768 781 794 807

and commented out
HorizSync	30-95
VertRefresh	50-160
from my xorg.conf


Once I reboot it gives me the option to run at 100 but the screen is all crushed (horizontally)  and doesn't look how it does under windows.

im loving playing with linux but my eyes just can't take it anymore

can someone please point out where i have gone wrong.

thanks
mentalinc


just another though it doesn't look like 1024*768 is there someother way to check it?

xdpyinfo | grep dimensions = dimensions:    1024x768 pixels (271x203 millimeters)

---

### Post by felipe on 2005-06-10
make sure you put the correct refresh/sync values for your monitor in xorg.conf (you can find them in the specs/manual you vendor should have supplied, or on the internet)

this could help: copy/paste this URL in firefox to get a modeline generator
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

---

### Post by skoal on 2005-06-10
You don't want to comment out your HorizSync and VertSync settings.  Just use this 'gtf' command to calculate your modeline and it should work (for example):
```
skoal@morpheus://~ $ gtf 1024 768 100 -x

  # 1024x768 @ 100.00 Hz (GTF) hsync: 81.40 kHz; pclk: 113.31 MHz
  Modeline "1024x768_100.00"  113.31  1024 1096 1208 1392  768 769 772 814  -HSync +Vsync
```

\\//_

---

### Post by mentalinc on 2005-06-10
thank you very much

Modeline "1024x768_100.00"  113.31  1024 1096 1208 1392  768 769 772 814  -HSync +Vsync

that modeline  (make sure you actually add -HSync +Vsync to the end of line line)

works like a charm

1024*768 at 100 now works 

except when i restart Gnome it ends up at 85 again

how do i make it default to 100?

/etc/X11/xorg.conf

note: i have removed all the comments from the top below

```

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
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
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 Ultra]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"Coolbits" "1"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	30-95
	VertRefresh	50-160
	Modeline "1024x768_100.00"  113.31  1024 1096 1208 1392  768 769 772 814  -HSync +Vsync
	DisplaySize	270	203	# 1024x768 96dpi
	Option		"DPMS"

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 Ultra]"
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
		Modes		 "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		 "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		 "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		 "1024x768" "800x600" "640x480"
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

```

---

### Post by skoal on 2005-06-10
That's a good question.  I guess you could try modifying your screen resolution modes like this:

Modes		 "1024x768_100.00" "1024x768" "800x600" "640x480"

and see if that uses the 100Hz refresh first.

\\//_

---

### Post by mentalinc on 2005-06-10
im an idiot

so no what you suggested didn't fix it.

under the options in screen resolution i had ticked make this my default (as it kept making windows XP use 85 as soon as i got rid of that after a reboot it worked.


so your instructions worked perfect just i had a tick in the wrong box.


thank you very much

---

