---
title: "Does anyone use a 4 monitor setup in ubuntu?"
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by reesh on 2007-01-20
I'm currently trying to port our office computers to ubuntu 6.10, but we have quad display computers here, and they are pretty much indispensable. does anyone run a quad setup in ubuntu or other linux distros? the video cards we use are Matrox g450 MMS. 

i've been trying to get at least 2 monitors working using both xinerama and Merged FB, as i understand they are the two options i have with a matrox card. 
MergedFB didn't work at all, but i had some intersting results with xinerama. after editing the xorg.conf file it seems that ubuntu recognises the dual monitor setup, because the workspace icons on the bottom right change from squares to long rectangles, indicating that the dual monitors are being used. but when this happens the second monitor remains blank, and changing  monitors, cables and video cards hasn't helped at all. 

any suggestions would be greatly appreciated, since i would love not to rely on windows anymore for the office boxes. i can post a copy of the xorg.conf file if requested, although i'm pretty sure it's a problem with the quad display capability, and i've checked xorg.conf for errors lots of times, and after all one of the monitors works (the primary) as described above

---

### Post by RandomJoe on 2007-01-20
Yep!  I did that!  I don't use it on a regular basis, but I did get it set up and working "just because I could".  Normally I only use three monitors.

I have two dual-head nVidia cards, and I'm using Xinerama to put them all together.  Worked a treat.  I had the fourth monitor propped up on the windowsill above my others, and actually had X configured to have it above the center screen.  I was able to drag stuff up and down to it, or side-to-side to the two other screens.  

This is on Ubuntu 6.06.

I have never tried MergedFB, don't know anything about it...

Since the workspace switchers are showing the elongated screen, it certainly sounds like you already got the X config mostly-right.  I've never had that sort of issue come up though - if I couldn't get a secondary screen working, then X also didn't show it active.

I don't think it's your issue (are the Matrox cards quad-head?) but I did stumble across one issue that was driving me batty.  You can specify "Screen X" in both the Device sections, and the ServerLayout section.  But they are for logically different things!  In the Device sections, it refers to which physical connector of a given card that Device is for, while in the ServerLayout it's a consecutive numbering of ALL the screens.  I at first thought both were supposed to be consecutive numberings, and X kept saying "no matching Device found".

Here's the relevant portion of my X config.  To enable the fourth display, I just have to uncomment the Screen 3 line in ServerLayout.
```
Section "Device"
        Identifier      "card1fp1"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Screen          0
EndSection

Section "Device"
        Identifier      "card1fp2"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Screen          1
EndSection

Section "Device"
        Identifier      "card2fp1"
        Driver          "nvidia"
        BusID           "PCI:8:0:0"
        Screen          0
EndSection

Section "Device"
        Identifier      "card2fp2"
        Driver          "nvidia"
        BusID           "PCI:8:0:0"
        Screen          1
EndSection

Section "Monitor"
        Identifier      "center"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "right"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "left"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "spare"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "centerScreen"
        Device          "card1fp1"
        Option          "UseDisplayDevice" "DFP"
        Monitor         "center"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "rightScreen"
        Device          "card2fp1"
#       Option          "UseDisplayDevice" "CRT"
        Monitor         "right"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "leftScreen"
        Device          "card2fp2"
#       Option          "UseDisplayDevice" "CRT"
        Monitor         "left"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "spareScreen"
        Device          "card1fp2"
        Monitor         "spare"
        DefaultDepth    24
        SubSection      "Display"
                Depth   24
                Modes   "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Multi-Screen"
        Screen          0 "centerScreen" 0 0
        Screen          1 "rightScreen" rightof "centerScreen"
        Screen          2 "leftScreen" leftof "centerScreen"
#       Screen          3 "spareScreen" leftof "leftScreen"
        Option          "Xinerama" "true"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection


```

---

### Post by reesh on 2007-01-21
thanks for the reply, i looked at your xorg file and there's nothing in it that would change my settings. i am starting to think that the video card isn't installed properly to enable the displays, it must be running in some default mode. what is the command to check if your video card is installed properly? 

i downloaded the linux drivers from the matrox site, but i can't install them in ubuntu. anyone know of a tutorial page that i can follow to get them working?

---

### Post by reesh on 2007-01-21
i just ran lspci | grep -i matrox and this is the output i get:

03:00.0 VGA compatible controller: Matrox Graphics, Inc. G400/G450 (rev 85)
03:04.0 Display controller: Matrox Graphics, Inc. G400/G450 (rev 85)
03:08.0 Display controller: Matrox Graphics, Inc. G400/G450 (rev 85)
03:0c.0 Display controller: Matrox Graphics, Inc. G400/G450 (rev 85)

it seems like the first controller is installed differently than the other 3, anyone have an idea why? when the card is installed in windows xp, the driver is installed 4 times, once for each controller, maybe i need to do something similar in ubuntu. 

any feed back is appreciated

---

### Post by RandomJoe on 2007-01-21
Have you tried using each of the four different PCI IDs that listing gives you, one for each Display?  (And each would also be Screen 0 for each display.)  Perhaps that card is actually four separate "cards" on one board...

On the other hand, if you _did_ do the above, have you tried using the first PCI ID in every Display section, then setting each one to Screen 0 thru Screen 3?  This is apparently how ATI cards work - they show multiple PCI IDs, but those are only used by the Windows driver.  (At least I think that's what I read!...)

I don't know of any commands to check the card is installed correctly.  I just ran lspci to get the PCI IDs and as far as I know if it shows up there it's ready to go.  I suppose it's possible there's some bit that needs to get flipped in the card before it works multi-head but I'm afraid I don't know anything about Matrox cards, never had one...

---

### Post by reesh on 2007-01-21
Well, i think you may have hit a nerve there... the other screens are actually coming on when i changed the PCI id to the corresponding value, and set the screen# to 0 on all of them. it's the first progress i've made in a while, thanks!



now while trying to get some output on the screen, i changed the color depth in the xorg.conf file, and the monitors change patterns (clear for 24 bit, thin vertical lines for 16 bit and thicker vertical lines for 8 bit). changing the resolution does not affect the other 3 monitors, but the main working monitor is changing accordingly



this is my relevant xorg.conf:

```
Section "Device"
	Identifier	"0_Matroxg450mms"
	Driver		"mga"
	BusID		"PCI:3:00:0"
	Screen		0
	Option		"OldDmaInit"		"True"
	Option 		"DDCMode" "True"
	Option 		"MonitorLayout" "LFP, LFP, LFP"
	Option      "MGASDRAM"
EndSection

Section "Device"
	Identifier	"1_Matroxg450mms"
	Driver		"mga"
	BusID		"PCI:3:04:0"
	Screen		0
	Option		"OldDmaInit"		"True"
	Option 		"DDCMode" "True"
	Option 		"MonitorLayout" "LFP, LFP, LFP"
	Option      "MGASDRAM"
EndSection

Section "Device"
	Identifier	"2_Matroxg450mms"
	Driver		"mga"
	BusID		"PCI:3:08:0"
	Screen		0
	Option		"OldDmaInit"		"True"
	Option 		"DDCMode" "True"
	Option 		"MonitorLayout" "LFP, LFP, LFP"
	Option      "MGASDRAM"
EndSection

Section "Monitor"
	Identifier	"MAG_0"
	Option		"DPMS"
	HorizSync    31.5 - 65.0
	VertRefresh  50.0 - 85.0
EndSection

Section "Monitor"
	Identifier	"MAG_1"
	Option		"DPMS"
	HorizSync    31.5 - 65.0
	VertRefresh  50.0 - 85.0
EndSection

Section "Monitor"
	Identifier	"MAG_2"
	Option		"DPMS"
	HorizSync    31.5 - 65.0
	VertRefresh  50.0 - 85.0
EndSection

Section "Screen"
	Identifier	"First_Screen"
	Device		"0_Matroxg450mms"
	Monitor		"MAG_0"
	DefaultDepth	24

	SubSection "Display"
		Depth		24
		Modes		"1280x1024" 
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Second_Screen"
	Device		"1_Matroxg450mms"
	Monitor		"MAG_1"
	DefaultDepth	24

	SubSection "Display"
		Depth		24
		Modes		"1280x1024" 
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Third_Screen"
	Device		"2_Matroxg450mms"
	Monitor		"MAG_2"
	DefaultDepth	24

	SubSection "Display"
		Depth		24
		Modes		"1280x1024" 
	EndSubSection
EndSection

Section "ServerFlags"
    Option "Xinerama"
EndSection

Section "ServerLayout"
	Identifier	"Multi_screen"
	Screen      	0 "First_Screen"
	Screen       	0 "Second_Screen" RightOf "First_Screen"
	Screen       	0 "Third_Screen" RightOf "Second_Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	#Option "Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

PS, i haven't added the actual 4th monitor yet, i dont' see the point until i get the others working, that's why there is no code for it

---

### Post by ggv6 on 2007-02-07
Hi,

I had the same problems and now can display lines on the second monitor. However I do not seem to be able to extend the desktop to use the second monitor. Xinerama does not seem to have any effect at all. The same problem even if I try to clone the desktop.

Has anyone managed to do this?

I would appreciate any help.
Thanks

---

