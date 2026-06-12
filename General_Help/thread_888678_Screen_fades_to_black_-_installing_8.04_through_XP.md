---
title: "Screen fades to black - installing 8.04 through XP SP2 on Fujitsu Lifebook 1120"
date: 2008-08-13
forum: General Help
---

### Post by atomic1973 on 2008-08-13
Hi all,

I was recently given a Fujitsu Lifebook 1120 ultraportable with a floppy drive but no CD.  My hope was to run Hardy on it but needed to put XP on as well.  Tried all weekend to work out a dual-boot system (tough with no CD drive... and it won't boot from USB drive) so I was elated to find Wubi.

Anyway, XP is on and I'm using Wubi to install Hardy.  The only error I get is that I've got 239MB of RAM free and it requires 256.  The error I'm having doesn't look like it's a memory issue, but I'd appreciate any feedback.

The process is fine for the most part, but after some time in the install (as it's confirming the install and creates partitions, etc) the screen fades to black from the Hardy desktop image.  It's a quick fade, but the mouse pointer is left on the screen so it's not a matter of the monitor going to sleep or a screensaver.  No amount of keyboard bashing or mouse movement will bring it back.

Incidentally, when I restart, XP starts up fine again (I mention that as other posts about the screen fading to black say that their Windows installs didn't work after that happened to them).

There was another post that said they got around this by installing in "safe mode".  I tried and got the same result as before.  I also get it when I try to run the Read Only from the Live CD.

The Lifebook has a built in ATI vid card... although I don't think it's a video card issue since when the screen is visible, it's clear and appears to have no issue.  Driver issue, perhaps?

I'd appreciate any insight anyone may have.  I apologize if this has been asked before.  I've been through the forums and others several times in the hopes of turning up something new, so I ask as a last resort.

Thanks!
Atomic....

---

### Post by Knoal on 2008-11-23
I have a "similar but different" issue:

I have a fresh install of HH.

I'm using the intergated ATI graphics (3200) on a Asus M3H/HDMI board

The screen fades to black after 60 second of no kbd/mouse activity.

No amount of keybd pounding or mouse moving will bring it back, although the raster (screen crackles with static) will come back on, but no image.

The screensaver is enabled, but never appears (60 seconds).

I have installed the newest ATI cataylist with Envy.

Do I need and xorg update?  A new version came out 8/23/08


xorg.config

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

:confused::confused::confused:

TIA


Knoal

---

### Post by ago on 2008-11-25
> **atomic1973 said:**
> 
Anyway, XP is on and I'm using Wubi to install Hardy.  The only error I get is that I've got 239MB of RAM free and it requires 256.  The error I'm having doesn't look like it's a memory issue, but I'd appreciate any feedback.
That is because part of the memory might be dedicated to the video card or other uses and hence only 239 is actually available.

> 
The Lifebook has a built in ATI vid card... although I don't think it's a video card issue since when the screen is visible, it's clear and appears to have no issue.  Driver issue, perhaps?
Do you mean the brightness is off (as in no backlight)? You might want to search this forum for the specific make and model of your video/laptop (use lspci). It is not likely to be a wubi specific issue.

---

