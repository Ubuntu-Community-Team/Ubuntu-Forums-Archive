---
title: "nVidia TwinView not working under Gutsy--  EDID problem?"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by Paradoxdruid on 2007-10-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/155001](https://bugs.launchpad.net/bugs/155001) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I just upgraded to Gutsy, which went off perfectly, except for one problem...

nVidia twinview isn't working for me anymore.  I have a analogue flat panel and a digital flat panel, both connected through DVI slots in my nVidia 7600 card (the analogue panel uses an adaptor).  Under Feisty, twinview worked perfectly, with both at 1280x1024 resolution.

Now, under Gutsy, the CRT connected monitor works perfectly fine (1280x1024) but the DFP goes to 640x480 resolution if I let nvidia-auto-select the metamode in xorg.conf, or it shuts off entirely if I specify a metamode like "1280x1024,1280x104".

A relevent chunk of my X log, with the 1280x1024 size stipulated:
> 
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
(**) NVIDIA(0): Option "SecondMonitorHorizSync" "31 - 80.0"
(**) NVIDIA(0): Option "SecondMonitorVertRefresh" "56 - 76"
(**) NVIDIA(0): Option "MetaModes" "1280x1024,1280x1024"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device DFP-1
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GT (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.51.04
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GT at PCI:1:0:0:
(--) NVIDIA(0):     Proview Radius-73 (CRT-0)
(--) NVIDIA(0):     DFP-1
(--) NVIDIA(0): Proview Radius-73 (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-1: Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Devices: CRT-0, DFP-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024,1280x1024"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024


So it sees both display devices (CRT-0 and DFP-1), but is unable to read the EDID info for the DFP.  It validates trhat 1280x1024,1280x1024 is a good mode, but then sets the virtual screen size to only 1280x1024, so the DFP shuts off.

If I instead specify nvidia-auto-select in the xorg.conf, it sets the DFP to 640x480.  Going into the nvidia-settings program, it says that 640x480 is the monitors native resolution (which it is not).

However, if I add an option in xorg.conf to ignore EDIDFreqs, then **both** monitors go to 640x480.  What could I specify to fix my twinview?

**Thanks for any advice offered!**

Here's a relevant chunk of my xorg.conf (you can see many options I've tried, then commented out):
> 
Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7600 GT]"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Option         "TwinView" "True"
        Option "SecondMonitorHorizSync" "31 - 80.0"
	Option "SecondMonitorVertRefresh" "56 - 76"
	Screen	0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7600 GT]"
	Monitor		"Radius-73"
	Defaultdepth	24
	#    Option "UseEDID" "False"
	#Option		"ExactModeTimingsDVI"
	Option		"TwinViewOrientation"	"RightOf"
	#Option		"MetaModes"	"1280x1024, nvidia-auto-select"
	#Option "ModeValidation" "NoDFPNativeResolutionCheck"
	#Option         "ConnectedMonitor" "CRT, DFP"
	Option         "TwinView" "True"
	Option "SecondMonitorHorizSync" "31 - 80.0"
	Option "SecondMonitorVertRefresh" "56 - 76"
	#Option     "SecondMonitorHorizSync"   "UseEdidFreqs"
	#Option     "SecondMonitorVertRefresh" "UseEdidFreqs"
	Option         "MetaModes" "1280x1024,1280x1024"
	SubSection "Display"
		Depth	24
		Modes		"1280x1024@60"	"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1600x1200@65"	"1152x864@75"	"1600x1200@60"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection

---

### Post by Robyr on 2007-10-22
I have this same issue. Two flat panels, one VGA, one DVI. The one connected via DVI doesnt get a res of over 800x600, but the VGA connected box goes all the way to native 1280x1024.... This is really quite annoying since it works flawlessly with Feisty...

---

### Post by Paradoxdruid on 2007-10-22
Yeah, the fact that it worked flawlessly under Feisty is the really frustrating part, especially since I can't see what changed to cause the difference--  sure, the nVidia driver is a newer version, but nothing in the documentation suggests a change.  Especially since it correctly calculates the metamode, but then discards it for the smaller virtual screen size.

What's stranger is that on nvidia-auto-select, it _does_ use the monitor, but only at a 640x480 resolution, claiming that is native--  despite my monitor's OSD saying "current: 640x480 60 Hz.  For best results: 1280x1024 60 Hz." and the fact that it worked under Feisty.  *sigh*

Guess I'll go scan the threads and see if someone has found a solution.

---

### Post by Paradoxdruid on 2007-10-28
After days of trying different options, I found a way to "solve" my problem--

Connect my LCD using its VGA cable through a VGA-DVI adapter, instead of the DVI connection.  Then, nvidia-settings and nvidia-xconfig and all the rest work as they should, automatically setting it to 1280x1024 at 60 Hz.

Honestly, I can't tell much visual difference, except on small font text, where it seems a little less sharp.  But I shouldn't need to give up my DVI connection and use an adapter just to get the correct monitor resolution.  The real problem is still extent and needs fixing.

---

### Post by mynameisflorian on 2007-11-04
I had the same problem on my main monitor. It happened when I was playing with my xorg.conf. I tried everything imaginable with my configuration file until I gave up and tried the obvious -- RESEAT THE CONNECTION! For those of you that don't know the jargin, that's just a fancy way of saying unplug and replug the cable. I screwed both ends in tight and voila! Problem solved!

- Florian

---

