---
title: "Interesting video fix for external LCD on a Latitude D620"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by nutz on 2007-06-06
I recently picked up an LCD to replace my CRT. I use it as an external display for my Latitude D620...

When I first hooked up to the LCD I had to make sure to deactivate the modeline for my CRT as they have different resolutions and refresh rates. So I went in and changed my xorg.conf so the modeline matched what my new LCD would require to be at it's native resolution. After a restart of X to activate the new settings I noticed that the resolution was correct but the refresh rate was not. For some reason the modeline that I generated had affected the resolution and changed it to the correct value but not the refresh rate...

And as a result the picture was not centered on the LCD. Even using the displays auto adjust function would not properly center the picture. But yet the LCD did not complain about being out of it's native resolution as it would if that was the case. So I dug a little deeper and started tweaking my xorg.conf and this is what I eventually figured out...

For some reason the modeline that I generated decided that I needed a horizontal refresh of 70.85 for my preselected and specified vertical refresh of 65.00. Now this is where my LCD had a problem, it would not properly center the picture with a h sync that high. So it was now that I realized this modeline deal wasn't going to work for me because regardless of the v sync it would always choose a h sync that was just too high.

So I removed the modeline and restarted X, but that made no difference either. The resolution was unaffected and the picture was still not centered properly. This I thought was weird because without the modeline it should have just gone to some sort of default refresh rate at the resolution I selected but that isn't what it did. It somehow retained the modeline setting as if it was still there even though I knew I removed them and verified it.

So slightly puzzled by all this I figured to hell with it for now I will eventually figure it out. 

So I moved on and opened up Nvidia settings to see what it would say about the new display. While I was in there I decided to mess with the refresh rate a bit and see if this app could shed some light on this issue. I instantly noticed there was more than one option for the vertical refresh rate of 60. As I was trying each of the options for a v sync of 60 which were labeled like 60(1), 60(2) etc; I got one that worked!

So my original suspicions were correct! The h sync being too high was to blame because that was the difference between these different modes. They were all settings for a v sync of 60 but with different h sync values. I selected one with a lower h sync and the picture instantly lined up and centered exactly as it should. Now I had to figure out a way to enforce this without the use of a modeline, this is how I did it...

	Option         "metamodes" "CRT: 1680x1050_60_0 +0+0"

The option 1680x1050_60_**0** I think specifies the h sync option to choose in the list of available modes for that v sync range.

This was the final working xorg.conf...

Section "Monitor"

	Identifier	"Generic Monitor"

	Option		"DPMS"

EndSection



Section "Screen"

	Identifier	"Default Screen"

	Device		"nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"

	Monitor		"Generic Monitor"

	DefaultDepth    24

	Option         "metamodes" "CRT: 1680x1050_60_0 +0+0"

	SubSection     "Display"

        Depth       24

        Modes      "1680x1050"

    EndSubSection

EndSection


Adding the meta mode fixed it...

This is what Nvidia has written about the use of metamodes on this driver...

MetaModes 
MetaModes are "containers" that store information about what mode should be used on each display device at any given time. Even if only one display device is actively in use, the NVIDIA X driver always uses a MetaMode to encapsulate the mode information per display device, so that it can support dynamically enabling TwinView.
Multiple MetaModes list the combinations of modes and the sequence in which they should be used. When the NVIDIA driver tells X what modes are available, it is really the minimal bounding box of the MetaMode that is communicated to X, while the "per display device" mode is kept internal to the NVIDIA driver. In MetaMode syntax, modes within a MetaMode are comma separated, and multiple MetaModes are separated by semicolons. For example:
    "<mode name 0>, <mode name 1>; <mode name 2>, <mode name 3>"
Where <mode name 0> is the name of the mode to be used on display device 0 concurrently with <mode name 1> used on display device 1. A mode switch will then cause <mode name 2> to be used on display device 0 and <mode name 3> to be used on display device 1. Here is an example MetaMode:
    Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
If you want a display device to not be active for a certain MetaMode, you can use the mode name "NULL", or simply omit the mode name entirely:
    "1600x1200, NULL; NULL, 1024x768"
or
    "1600x1200; , 1024x768"
Optionally, mode names can be followed by offset information to control the positioning of the display devices within the virtual screen space; e.g.,
    "1600x1200 +0+0, 1024x768 +1600+0; ..."
Offset descriptions follow the conventions used in the X "-geometry" command line option; i.e., both positive and negative offsets are valid, though negative offsets are only allowed when a virtual screen size is explicitly given in the X config file.
When no offsets are given for a MetaMode, the offsets will be computed following the value of the TwinViewOrientation option (see below). Note that if offsets are given for any one of the modes in a single MetaMode, then offsets will be expected for all modes within that single MetaMode; in such a case offsets will be assumed to be +0+0 when not given.
When not explicitly given, the virtual screen size will be computed as the the bounding box of all MetaMode bounding boxes. MetaModes with a bounding box larger than an explicitly given virtual screen size will be discarded.
A MetaMode string can be further modified with a "Panning Domain" specification; e.g.,
    "1024x768 @1600x1200, 800x600 @1600x1200"
A panning domain is the area in which a display device's viewport will be panned to follow the mouse. Panning actually happens on two levels with TwinView: first, an individual display device's viewport will be panned within its panning domain, as long as the viewport is contained by the bounding box of the MetaMode. Once the mouse leaves the bounding box of the MetaMode, the entire MetaMode (i.e., all display devices) will be panned to follow the mouse within the virtual screen. Note that individual display devices' panning domains default to being clamped to the position of the display devices' viewports, thus the default behavior is just that viewports remain "locked" together and only perform the second type of panning.
The most beneficial use of panning domains is probably to eliminate dead areas -- regions of the virtual screen that are inaccessible due to display devices with different resolutions. For example:
    "1600x1200, 1024x768"
produces an inaccessible region below the 1024x768 display. Specifying a panning domain for the second display device:
    "1600x1200, 1024x768 @1024x1200"
provides access to that dead area by allowing you to pan the 1024x768 viewport up and down in the 1024x1200 panning domain.
Offsets can be used in conjunction with panning domains to position the panning domains in the virtual screen space (note that the offset describes the panning domain, and only affects the viewport in that the viewport must be contained within the panning domain). For example, the following describes two modes, each with a panning domain width of 1900 pixels, and the second display is positioned below the first:
    "1600x1200 @1900x1200 +0+0, 1024x768 @1900x768 +0+1200"
Because it is often unclear which mode within a MetaMode will be used on each display device, mode descriptions within a MetaMode can be prepended with a display device name. For example:
    "CRT-0: 1600x1200,  DFP-0: 1024x768"
If no MetaMode string is specified, then the X driver uses the modes listed in the relevant "Display" subsection, attempting to place matching modes on each display device.


So just wanted to share that. I am pretty new to Linux but this seemed to be worth sharing. The meta modes also solved the problem I was having on another workstation where the modeline in the xorg.conf was not working for one user but worked fine for the other users of that system. I removed the modeline from that workstation and replaced it with a metamode and now it displays the correct resolution for all users.

Any thoughts?

---

