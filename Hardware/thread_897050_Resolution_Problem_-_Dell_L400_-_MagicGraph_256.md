---
title: "Resolution Problem - Dell L400 - MagicGraph 256"
date: 2008-08-21
forum: Hardware
---

### Post by LegndLarry33 on 2008-08-21
Hi,

I have tried everything, and I can't seem to get my screen resolution higher than 800x600.  I have tried everything here:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

A sign that I'm pretty sure something is screwed up good is that I don't seem to get the prompt asking if I want to autodetect video hardware when I run "sudo dpkg-reconfigure xserver-xorg".

My xorg.conf is very short and the monitor section just list "generic":

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

I have downloaded "xserver-xorg-driver-neomagic_1.0.0.5-0ubuntu1_i386" but it fails when I try to install it and tells me something about "conflicting pakages"...

I get the impression that the drivers are not installing, but I can't seem to figure out how to install them. Any help would be very much appreciated.  I'm going crazy over here.  Thanks!

---

