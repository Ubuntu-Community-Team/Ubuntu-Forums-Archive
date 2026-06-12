---
title: "external monitor problem (dell latitude d610)"
date: 2008-11-15
forum: Hardware
---

### Post by Daklin on 2008-11-15
I just got an external monitor (Vizio VX20L) that I want to use as my main desktop monitor.  However, I can't get Ubuntu to natively switch to the widescreen resolution 1280x768, it's stuck at 1024x768.  I tried editing xorg.conf with no luck, as I'm pretty new at this.

Running 8.04, using xserver-xorg-video-intel (not i810).  I want to be able to swtich resolutions between 1024x768 and 1280x768 manually, so that I can use the smaller one when I'm unplugged from the Vizio monitor.  How should I edit xorg.conf?  Included the relevant sections, which I've left untouched from my failed attempts.

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
	Option		"LinearAlloc"		"6144"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

