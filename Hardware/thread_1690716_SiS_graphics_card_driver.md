---
title: "SiS graphics card driver"
date: 2011-02-18
forum: Hardware
---

### Post by dormant on 2011-02-18
I'm using Ubuntu 10.10 on an old Asus Pundit SFF PC, which uses an SiS graphics card. I've lost the documentation telling me exactly which card it is.

Quite a few releases ago, I took a lot of trouble to install a driver for this, downloaded from [www.winischofer.net](www.winischofer.net). That driver doesn't seem to be supported in the repositories anymore.

At the moment, I don't seem to be using any special driver. System-Preferences-Monitor detects an Unknown monitor. System-Information-Additional Drivers detects nothing.

Graphics response on this machine has been sluggish for a while, and I now find I need to improve it. My questions here are:

[LIST=1]
[*]Am I using the correct driver for my graphics card?
[*]If not, how can I install it?
[/LIST]

Here is some info that might help. I used to know a lot more about the nuts and bolts of Linux, and I guess it's a sort-of compliment to the distro that I am rusty because I haven't done anything systemmy like this for a while. This is my media-centre PC, and I don't really do much to it except upgrade software when it tells me to. 
 
Synaptic reports three packages are already installed:
[LIST]
[*]xserver-xorg-video-sisusb
[*]sisctl
[*]xserver-xorg-video-sis
[/LIST]

The relevant bit of my xorg.conf looks like this:
```

Section "Device"
	Identifier	"Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL 2407WFP"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter"
	Monitor		"DELL 2407WFP"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1920x1200" "1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

```

I also see a couple of threads here that talk about using a totally different driver for SiS cards.

---

