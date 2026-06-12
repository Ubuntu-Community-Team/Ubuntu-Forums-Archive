---
title: "HP Compaq nc6120 (8.10) and 915GM driver."
date: 2008-12-29
forum: Hardware
---

### Post by Xb0x3r on 2008-12-29
I've tried searching but I just couldn't find a fix for my problem.

I have the HP Compaq nc6120 running Intrepid Ibex and I cannot figure out why my video drivers will not work. I am trying to play Counter-Strike through Wine (which is supposed to work full screen) and all it does is go to a black screen and it just sits there. I'm convinced that it is not using my video driver and looking at my xorg.conf proves this to me. Here's my xorg.conf file

> Section "Device"
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

Even though my i810 driver is installed it is not being used and it seems like nothing at all it being used to run the video. But somehow its working when I'm doing normal things (I'm typing this right now on the said laptop).

Any advice?

---

### Post by Xb0x3r on 2008-12-30
Bump :P

---

### Post by Xb0x3r on 2009-01-02
Anybody have any ideas?

---

### Post by Don Heard on 2009-02-24
I can't say about gaming but I have found in some video players that I get a black screen to start with but if I change to full screen I see the video and if I restore to original size it works fine.  It is only on startup that I have a black screen.

---

