---
title: "Ghostly nvidia graphics drivers"
date: 2008-11-03
forum: General Help
---

### Post by ems5311 on 2008-11-03
Hi,
I just ran a fresh install of Ubuntu 8.10 **64 bit** on a Sager NP2096 (2.4 ghz dual core, nvidia 9600, 4 GB ram).  The reason for this was I could not get wireless working otherwise.  Wireless works now, but I cannot get my Nvidia drivers working.  Problem is, it *says* that they're working, though I have reasons to believe they are not.

I have everything in nvidia-settings jacked up to full volume (anti-aliasing, texture sharpening, image settings at full), but my desktop looks choppy and runs poorly when I use compiz effects, or have lots of programs open at once.  I know they are not working properly because in 8.04 32 bit everything looked much, much nicer.

Something is puzzling me about xorg.conf.  Here is my xorg.conf:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

There's almost nothing there.  I remember in 8.04 this file was filled with stuff.  Is that just the way this system is structured, or is this the problem?

Also, when I hold super-ctrl, my xserver crashes.  I discovered this because I was trying to do the rain effect in compiz, but even after I turned that off this is still happening.  This is annoying because I can accidentally hit those two keys and screw everything up.

Like I said, all my repositories and drivers are installed and claim to be working.  I am very saddened by this because everything seemed to be running so well when I installed and saw the wireless was working.  I tried installing a different driver (173 instead of 177) with envy but nothing changed (also gives me reason to believe my drivers aren't being recognized at all).

Anyone know any commands or tests I can run that will give me definitive evidence as to whether my cards are working or not?  Anyone else experiencing this problem?  Any help will be appreciated.  Thanks in advance.

---

### Post by pansz on 2008-11-03
generally, run the command 'glxinfo' in terminal will give you most ideas about whether the driver working or not.

I'm using 8.04 64bit with the same nvidia card and everything works. So I think it might be a 8.10-specific problem. Well, I won't use 8.10 anyway.

My suggestion: copy the working version of xorg.conf from your 8.04 to the current 8.10, this may solve many problems. -- I used to have x problem in 8.04 and I copied the xorg.conf from 7.10 to 8.04 and problem solved.

---

