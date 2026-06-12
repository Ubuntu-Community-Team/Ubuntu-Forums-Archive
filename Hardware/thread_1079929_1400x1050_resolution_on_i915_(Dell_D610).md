---
title: "1400x1050 resolution on i915 (Dell D610)"
date: 2009-02-24
forum: Hardware
---

### Post by 12261980 on 2009-02-24
I am running Ubuntu 8.10 on Dell D610 laptop with i915 graphic chipset. I would like to be able to run 1400x1050 resolution.

BIOS is version A05. I have the latest Intel drivers installed as part of the xserver-xorg-video-intel package. My xorg.conf looks like this:

Section "Device"
           Identifier "intel"
           Driver     "intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"intel"
	Monitor		"Configured Monitor"
	Device		"intel"
EndSection


Can someone help me? (Please assume I have no knowledge on Ubuntu, given I installed it just a couple of weeks ago).

---

