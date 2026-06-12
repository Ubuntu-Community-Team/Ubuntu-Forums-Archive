---
title: "Problem With Dual Monitor Display Settings"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by The Recorder on 2009-05-17
Just installed the Xubuntu Desktop on a Jaunty machine that already has Ubuntu and Kubuntu installed.  Everything is working OK, except that I have two (2) monitors, and Display is only showing one (1) monitor.  This is NOT the case in Ubuntu and Kubuntu, and in Ubuntu I am even able to get a Big Destop (2048x768) and Compiz running, even though I have an older ATI card (Radeon x700) and am using the open-source ATI drivers.

What is odd is that when I bring up Desktop Settings (in Xubuntu) it shows tabs for "Monitor 1 (DVI-1)" and  "Monitor 2 (DVI-2)".  Of course, since Xfce Display is only recognizing one (1) monitor, the settings in each tab affect both monitors.

My "xorg.conf" file is a simple one:

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2048 768
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"True"
EndSection

Fearing that I might mess up my Ubuntu and Kubuntu setups, I am a little afraid to change anything in the "xorg.conf" file.

Does anyone have any ideas on what I might do to get the second monitor to show up in Xubuntu?

Thanks much,

The Recorder****

---

### Post by pavl74 on 2009-05-18
I have exactly the same problem. In ubuntu everything works fine... but not in Xubuntu...

Anyone an idea?

---

### Post by The Recorder on 2009-05-18
I used the following as my "xorg.conf" file.  Save your present "xorg.conf", and then replace the following for what you have.  Depending on your setup, you may have to make some changes to the "Virtual", "Device" "options" 2 & 3, and all the entries in the two (2) "Monitor" sections - I had to.  It took a few tries, but I finally got it to work; and everything works great.  All the credit goes to the poster mentioned at end of this post.

*************

Section "ServerLayout"
        Identifier      "Dual Head Layout"
        Screen          0       "Default Screen"        0 0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 3200 1200
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "monitor-DVI-I_2/analog"        "DVI-0"
        Option          "monitor-DVI-I_1/analog"        "DVI-1"
        Option          "RROutputOrder"                         "DVI-I_2"
EndSection

Section "Monitor"
        Identifier      "DVI-1"
        Option          "Position"      "1280 0"
EndSection

Section "Monitor"
        Identifier      "DVI-0"
        Option          "LeftOf"        "DVI-1"
EndSection

Section "ServerFlags"
        Option  "DontZap"       "True"
#       Option  "Xinerama"      "True"
EndSection

*************

Last edited by isilmeraumo; 2009-05-12 at 11:38 AM CDT.

---

### Post by n888 on 2009-05-19
Ran into the same issue you did, started off with Ubuntu Desktop 9.04, installed xubuntu-desktop package afterwards. Could see the extra monitor under 'Desktop' but not 'Display'.

Just had to comment out the existing Monitor section and add the two monitor sections. The virtual section was already there from the gnome setup.

#Section "Monitor"
#	Identifier	"Configured Monitor"
#EndSection

Section "Monitor"
Identifier "DVI-1"
Option "LeftOf" "DVI-0"
EndSection

Section "Monitor"
Identifier "DVI-0"
Option "Position" "1440 0"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2880 900
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

---

### Post by furzd on 2010-07-29
I had a problem with Ubuntu 8.04 with Dual monitors.
I could not disable the clone option.
this helped me a lot!

tx!!

---

