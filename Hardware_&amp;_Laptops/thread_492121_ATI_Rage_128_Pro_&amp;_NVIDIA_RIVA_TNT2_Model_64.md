---
title: "ATI Rage 128 Pro &amp; NVIDIA RIVA TNT2 Model 64"
date: 2007-07-04
forum: Hardware &amp; Laptops
---

### Post by stephenlittleton on 2007-07-04
Okay, so I have these two crappy graphics cards, and I'd like to get them working.

When i started, I had opengl.  I could view the matrix opengl screensaver no problem.  When i clicked test.  When it came on after the timeout, the screen would flicker really fast... looked horrible and painful for my computer...

Now I cannot get anything to work.  Not even huffo's tunnel screensaver.

I tried installing and uninstalling and configuring and reconfiguring... There seems to be a couple of us stranded out there trying to use these cards.  

One guy said he used the restricted modules and got his nvidia logo up, I tried the same steps and got nothing.  Another guy said he got his working automatically with the ATI card, I have both cards, and have been working on this for around a month and a half now.  I have given up the idea of playing Beryl or installing emerald themes, this i Know. 

But I just want to have some kind of hardware acceleration for movies and to play quake 1 and 2...

Any help here would be GREATLY appreciated.

Oh, and each time with the nvidia card, I get error 104, cannot load nvidia kernel, no sutible screens found, etc etc, then i change nvidia to nv in xorg.conf and it works.  I even did the commenting of DRI and GLX.  All different ways.  If I put it to NVIDIA it fails.. even with the legacy restricted modules.

The ATI card "seemed" to work, that is I got COMPIZ to stay on as my desktop manager, and it looked a lot faster.  But then I reinstall from scratch and compiz freezes, no window manager at all, and I have to restart x sometimes.

---

### Post by stephenlittleton on 2007-07-04
A little Updates on the NVIDIA Card... I know you need the log files, so here they are.

=====:[  This is the one that works, the NV Driver But look...  ]:=====

(==) NV(0): Write-combining range (0xfc000000,0x2000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(==) RandR enabled

..........other modules loading snipped out...............

II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard

---

### Post by jrusso2 on 2007-07-04
You need to look and see what cards those drivers support and I am pretty sure they don't go back to those old cards.

---

### Post by stephenlittleton on 2007-07-22
I figured it out.  I did a lot of research on the matter and ended up needing the nvidia binary driver from their site.  Its listed in the readme file.

I uninstalled, reinstalled, disabled glx, and re-enabled it... several times in different combinations.  Finally it just worked, nvidia logo, glx is enabled, and I can look at the fireworks screensaver and muse in its glory!

But the key was adding a line of code and installing the binary, its all in another guide somewhere off of ubuntuforums.org ...

Took forever to figure out what was going on, but, i am glad I did.

---

### Post by Soulkipper on 2008-01-12
> **stephenlittleton said:**
> I figured it out.  I did a lot of research on the matter and ended up needing the nvidia binary driver from their site.  Its listed in the readme file.

I uninstalled, reinstalled, disabled glx, and re-enabled it... several times in different combinations.  Finally it just worked, nvidia logo, glx is enabled, and I can look at the fireworks screensaver and muse in its glory!

But the key was adding a line of code and installing the binary, its all in another guide somewhere off of ubuntuforums.org ...

Took forever to figure out what was going on, but, i am glad I did.

I'm a noob with feisty fawn. Just installed it a week ago and the experience is being thrilling! I love everything about it. But I have the same problem that you had with the video card cause its the same and i wanted to play with some compiz features...

 I don't want those fancy window effects, just the cube and to be able to change the desktop themes. Could you help me with the code lines and such? For exemple, how do I edit the Xorg file?

---

