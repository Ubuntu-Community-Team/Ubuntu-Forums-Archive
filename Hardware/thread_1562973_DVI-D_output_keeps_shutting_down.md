---
title: "DVI-D output keeps shutting down"
date: 2010-08-28
forum: Hardware
---

### Post by Peter Bell on 2010-08-28
I have just completed building a new machine:

i5-650 in an Intel DH55HC motherboard.  I'm using the on-board graphics driving my ViewSonic VP2030 display from the DVI-D socket.

I've installed standard Ubuntu Lucid 64bit on this machine and find that the monitor repeatedly and relatively frequently will report 'no signal'.  I normally run in 1600 by 1200 mode.  I've read other threads where it is reported that there is, occasionally, a 'no signal' condition from boot.  This doesn't reflect my situation at all - the video has always started up perfectly well from boot ... it just vanishes some time later (perhaps a minute, sometimes a couple of hours).  Usually, I can get the signal to reappear by switching the display to standby, and back on ... sometimes just by switching inputs momentarily (that's the English 'momentarily', not the American meaning!).  However, it is extremely annoying when the screen keeps disappearing at frequent, but irregular, intervals.

At first I suspected a hardware problem (poor connection?), however the results of my testing would suggest otherwise.

I've tried using an hdmi - dvi-d adaptor, and driving the display from the hdmi port on the motherboard.  The problem simply does not occur in this configuration.  I also have Win XP home (SP3) installed, and the problem does not occur.  I've tried booting a simple slackware installation - again, the problem does not occur.

Does anyone have any thoughts on this, or any advice to work around it?

I also wonder whether this has any connection with the problem I am experiencing on another machine - a Shuttle X-200B, Core 2 (T5200) processor, driving a ViewSonic VP181 via DVI-D, from the onboard 945 video.  This system, sometimes reports that the display unit cannot be identified and that it's switching to low-resolution mode (actually, the resolution stays the same, at 1280 by 1024, but screen updates become very noticeably slower).  As this occurs, all running applications are aborted.  This system started at 6.10 and has been regularly updated to current 10.04.  The current symptoms only started with 10.04.

I wonder whether Ubuntu regularly probes the display to report its capabilities and the response sometimes gets lost, or misinterpreted, whereupon the O/S decides to shut the video down.

---

### Post by Peter Bell on 2010-08-29
I've been doing some more investigation, and it looks as though my idea that the display is being probed regularly may be correct.

If I look in Xorg.1.log, I can see that the display is set up while other devices are being configured, with EDID info being reported.

Then, after what appears to be initial configuration, there are eleven more occurrences of EDID information being reported.  Unfortunately, because there is no time stamping, I can't tell how often/regularly this is happening.

I'm a little puzzled that the following is reported within the log:

```
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output HDMI1 disconnected
(II) intel(0): Output HDMI2 connected
(II) intel(0): Output DP1 disconnected
(II) intel(0): Output DP2 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output HDMI2 using initial mode 1600x1200

```

Something believes that my system has two HDMI ports, and two DVI ports?

I know that the DVI-D connection can carry two separate ports - is this also true of HDMI?

More puzzling is that it is being reported that HDMI2 is connected whan I'm sure that this log relates to a time when I was using the DVI-D connection.

Other posts refer to modifying xorg.conf in order to control behaviour of the video support.  However, I cannot find /etc/X11/xorg.conf.

Does any of this info provide clues as to why the problem is happening, and how I can fix it?

---

### Post by Peter Bell on 2010-08-29
Okay, I've now created an xorg.conf by going into safe mode - now I have to work out what to put in the Monitor, Device and Screen sections.

---

### Post by Peter Bell on 2010-09-01
I've finally got to the bottom of this issue, and fixed it.  I will jot down a few comments just in case they happen to help someone else who experiences similar problems.

The root of the problem was that the screen mode I was using was being generated with a 162MHz pixel clock rate - close to the DVI maximum of 165MHz.  For some reason my monitor was unable to lock onto this signal reliably - I'm not sure why .... perhaps the age of the monitor (five years), perhaps the high ambient temperature (usually in excess of 30C), perhaps a low quality DVI-D cable (it was the only one I could find in this city!), or perhaps a combination of all three!

I discovered that the intel driver was not creating a 'reduced blanking' mode definition (a technique which can be used with non-crt-based displays, to reduce the number of pixels generated for a frame).  I'm not sure whether this is because reduced blanking is not implemented in the intel driver, or because it decided that it was not necessary (or not possible?) for my monitor.

I used a program called cvt to generate the timings for a suitable reduced blanking mode : [CVT Calculator]("http://www.nvnews.net/vbulletin/showthread.php?t=60669")  The mode timings which were generated have a pixel clock of 130MHz - comfortably inside the maximum limit.

I then used the generated mode timings in a modified xorg.conf.  Finding out how to construct the appropriate entries for the conf file was not entirely obvious.  Neither man intel, nor man xorg.conf, gives all the information - some option entries appear to work in some sections of the conf file and not in others.  Some documented option values appear not to be implemented (in the intel driver?).  I resorted to some trial and error in order to arrive at a working solution.  The other stumbling block was that man xorg.conf says that a separate 'device' section is required for each head of a multi-headed video interface - this appears to apply to nvidia drivers, not the intel driver.  man intel gives an example of a multi-head device section, but the significance wasn't clear until I looked at further documentation for the intel driver on the xorg website.  For the intel driver, a single device section is used, with an option line to describe each head.

Anyway, the relevant parts of my new xorg.conf are as follows:

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen         "Screen0" 0 0
	Screen         "Screen1" 0 0
	Screen         "Screen2" 0 0
	Screen         "Screen3" 0 0
	Screen         "Screen4" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Device"
	Identifier      "Clarkdale"
	Screen		0
	Driver          "intel"
	VendorName      "Intel Corporation"
	BoardName       "Core Processor Integrated Graphics Controller"
	BusID           "PCI:0:2:0"
	Option		"monitor-VGA1" "VP2030bVGA"
	Option		"monitor-HDMI1" "VP2030bDVI"
	Option		"monitor-HDMI2" "VP2030bDVI"
	Option		"monitor-DP1" "VP2030bDVI"
	Option		"monitor-DP2" "VP2030bDVI"
EndSection

Section "Monitor"
	Identifier      "VP2030bDVI"
	VendorName      "ViewSonic"
	ModelName       "VP2030b"
	HorizSync       30.0 - 92.0
	VertRefresh     50.0 - 75.0
	modeline	"1600x1200@60R"   130.25 1600 1648 1680 1760 1200 1203 1207 1235 +hsync -vsync
	Option	        "PreferredMode" "1600x1200@60R"
	Option		"NoDDC"
EndSection

Section "Screen"
	Identifier 	"Screen2"
	Device     	"Clarkdale"
	Monitor    	"VP2030bDVI"
	DefaultDepth	24
	Option          "ExactModeTimingsDVI"
	Option		"IgnoreEDID"
	Option		"NoDDC"
	SubSection "Display"
		Depth     24
		Modes	"1600x1200@60R"
	EndSubSection
EndSection

This has now been running for 11 hours without once losing the signal.


Why did Windows not exhibit the problem?  I guess that it is using 'reduced blanking' timings by default.  Why did I not have the problem when using the HDMI output - perhaps my HDMI cable is better quality, perhaps there are other factors in the hardware, perhaps reduced blanking was being used automatically on the HDMI interface ... I don't know, but I will go back and investigate this at another time.

---

