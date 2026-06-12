---
title: "(Another) Widescreen tale of woe"
date: 2007-02-23
forum: Hardware &amp; Laptops
---

### Post by pbrockway2 on 2007-02-23
I am trying to get a Viewsonic VA1912wb monitor to display 1440x900 using an Intel 82865G graphics controller.

I've installed 915resolution and /etc/default/915resolution looks like this:
> #
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
#MODE=auto
MODE=3c
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1440
YRESO=900
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=32
/etc/X11/xorg.conf includes> 
Section "Device"
	Identifier	"Intel"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x1024" "1024x768"
	EndSubSection
EndSection
Everything seems to start up and I hear the GUI music, but all I see is a message from my monitor "Out of range: Horizontal frequency 42Khz, vertical frequency 28Hz".

If I remove the "1440x900" parts then I can see the screen fine - however 1440x900 is the resolution I want, and is the only ratio that is really tolerable on this monitor.

I've tried adding HorizSync 30-82 VertRefresh 50-85 to the monitor section.  And also another driver (i810_drv.so) from [http://www.fairlite.demon..co.uk/intel.html](http://www.fairlite.demon..co.uk/intel.html).  Neither makes any difference.

I've also tried sudo dkpg-reconfigure xserver-xorg which changes the mode lines and leads to the (unwanted) behaviour described above.

Have I missed something obvious?

I'd love a solution to drop out of the sky - but, failing that, I'd settle for some encouragement.  None of the threads I've read actually describe this combination (ViewSonic + onboard Intel graphics) working.  Is there anyone with this arrangement?  Or should I go shopping another monitor/graphics card?

---

### Post by mkuutti on 2007-02-24
see thread [http://ubuntuforums.org/showthread.php?t=363555]("http://ubuntuforums.org/showthread.php?t=363555")

---

### Post by pbrockway2 on 2007-02-24
Thanks mkuutti.

I've had a look at your thread, and also nicon's (to which you link).  

Following reply 10 in nicon's thread (using DDC to get the monitor characteristics, setting the modeline in xorg.conf, and your suggestion of adding HTOTAL and VTOTAL settings) leave me no further ahead.  My monitor reports "no signal" whenever the 1440x900 resolution is in use.

---

### Post by pbrockway2 on 2007-02-25
Straight after I last posted I realised that I had forgotten one thing:  I hadn't altered  /etc/init.d/915resolution so the changes I was making to the video were being (partially) lost when I reset.

Correcting this mistake I found that I *could* see 1440x900, but the display was odd: imagine the left and right hand sides of the monitor joined togther and the whole thing twisted so the "seam" appeared part way across the screen.

I tried various mode settings for 915resolution and nothing worked.  38, 49, and 58 
continued to give "no signal" and the others displayed the odd screen described above or a blank one.

Then I changed the xorg.conf Screen/Display subsection so that it had *only* the 1440x900 mode as in nicon's thread.  Eureka!

In case it's useful for anyone else with the  Viewsonic VA1912wb/Intel 82865G combination, here's what I'm using:

/etc/X11/xorg.conf
```
Section "Monitor"
	Identifier	"Generic Monitor"
	DisplaySize	410 256
	HorizSync	30.0-82.0
	VertRefresh	50.0-85.0
	Option 	      	"DPMS"
		# The above as reported by DDC
		# The modeline params are clock h_active h_sync h_sync_end h_blanking v_ditto
	Option		"DDC" "false"
	Modeline	"1440x900" 106.5 1440 1520 1672 1904 900 903 909 934 +Hsync +Vsync
EndSection
...
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel"
	Monitor		"Generic Monitor"
	DefaultDepth	24
...
	SubSection "Display"
		Depth		24
		#Modes		"1280x1024" "1024x768" "1440x900"
		Modes		"1440x900"
		ViewPort	0 0
	EndSubSection
EndSection
```
/etc/default/915resolution```
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
#MODE=auto
MODE=38
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1440
YRESO=900
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=24
HTOTAL=1904
VTOTAL=934
```

/etc/init.d/915resolution```
case "$1" in
  start|restart|force-reload)
	echo -n "Starting $DESC: "
	if [ "$MODE" = "auto" ] ; then
	    auto_select_modes
	else
	    # the last two arguments added to this line
	    $PROG $MODE $XRESO $YRESO $BIT $HTOTAL $VTOTAL
	fi
	echo "$NAME."
	;;
```

Thanks again mkuutti for the extra arguments that 915resolution accepts, and nicon for the suggestion (and example) of using DCC to obtain the correct monitor settings.

---

### Post by mkuutti on 2007-03-03
Thank **you**, I found my solution (which was not so technical at all), See my solution at: [http://ubuntuforums.org/showthread.php?t=363555]("http://ubuntuforums.org/showthread.php?t=363555")

---

### Post by sujeet on 2007-08-26
I followed your method exactly on identical hardware and am now getting 1600x1200 resolution on my monitor - still no 1440x900 even though that is the only mode listed in my xorg.conf! Any idea where I could be going wrong? Here's my xorg.conf:

# Xorg configuration created by system-config-display

Section "ServerLayout"
	Identifier     "single head configuration"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	ModelName    "LCD Panel 1440x900"
	HorizSync    30.0 - 82.0
	VertRefresh  50.0 - 85.0
	Option	    "dpms"
	Option		"DDC" "false"
	Modeline	"1440x900" 106.5 1440 1520 1672 1904 900 903 909 934 +Hsync +Vsync
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver      "i810"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1440x900"
	EndSubSection
EndSection

Thanks in advance for your help!

---

