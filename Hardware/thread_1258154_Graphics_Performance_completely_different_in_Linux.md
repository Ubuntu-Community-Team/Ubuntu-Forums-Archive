---
title: "Graphics Performance completely different in Linux than Windows"
date: 2009-09-04
forum: Hardware
---

### Post by themattbeballin on 2009-09-04
My Graphics Card (nVidia GeForce 6200LE 512MB) acts completely different in Windows than in Linux..

I don't currently know why this is... My Windows driver is the 180 version and so is my Ubuntu 9.04 one.

In World of Warcraft, I struggle to pull 30FPS in Linux, but in Windows I can easily pull 45-50 outside a major area.

In Second Life (Linux Version), I pull 5FPS, can't tell you why this is, because I do not know...

In the Second Life (Windows Version with WINE), I pull 10-15FPS though in Windows I bull 20-30FPS... 

I understand my video card is under the minimum requirements for Second Life, though I know that can't be the cause..

My WINE version is their latest development release.

Any help on why my graphics suck in Linux would be appreciated. 

Matt

---

### Post by 00arthuryu on 2009-09-04
You are running a game built for windows, not linux, Wine is a compatibility layer. The fact that it works at all is simply amazing.
The game you're playing uses DirectX, Wine "translates" this into OpenGL and then displays it. You are comparing a supposed windows only game working in windows to it working in linux.

If you want a game to compare, go for Unreal Tournament 2004 since it works natively on linux, I actually get more FPS on UT2004 on linux than on windows.

---

### Post by Gen2ly on 2009-09-04
Yeah for WoW you have to specify to use OpenGL which unfortunately isn't given as much attention to as DirectX by Blizzard.  If it was I think that comparision to Windows WoW with DirectX would be pretty close.

---

### Post by themattbeballin on 2009-09-04
WoW is set for OpenGL in my Config on both Windows and Linux. 

SecondLife RARELY uses DirectX from what I read.

---

### Post by dagoth_pie on 2009-09-05
You could try installing an older set of graphics drivers, the card predates those drivers by a few years doesn't it?

---

### Post by themattbeballin on 2009-09-05
I'm not sure.. I know when I ran the driver scan on nVidia's website on the Windows side of my computer it was recommending the 190 drivers... and I just did it on the linux side too and it's wanting the 190s too.

---

### Post by themattbeballin on 2009-09-05
The disk I got with the card contained the 170 drivers for Windows.

---

### Post by themattbeballin on 2009-09-05
Still needing help here... 

I'm on my Windows side right now, and actually hate it very much.. 

So anything to keep me from this side of my computer will be appreciated.

---

### Post by dagoth_pie on 2009-09-05
I can't say anything in particular will help, I'd say you may as well try downgrading drivers, if it doesn't make a difference you could try enabling agp fastwrite, I think thats what it was called, it'll only work if you have an 8x AGP slot though, if you "google enable agp fastwrite linux" it'll come up with a guide, also, apparently this has problems with VIA chipsets on the motherboards. But a guide will tell you that, good luck

---

### Post by themattbeballin on 2009-09-06
Thanks.. I'll give that a shot...

I've downgraded the drivers before.. 

But I'll enable fastwrite and see.

---

### Post by themattbeballin on 2009-09-08
Okay, well Fast Write did nothing... 

I got maybe .5FPS better at the most. 

But I also have ran into another issue, but that may be for another thread at another time.

--Edit--- The other issue has been fixed.. it was a HDD priority issue... I wasn't able to get to GRUB without the LiveCD until I hunted through the BIOS.

---

### Post by themattbeballin on 2009-09-08
Any other suggestions on the graphics issue?

---

### Post by dagoth_pie on 2009-09-08
Sorry, I'm all out of ideas, I know the 6200 is a low end card, maybe they optimized it for DX and left OpenGL out? I think you've tried everything I can think of. I can also tell you that card hates being overclocked, I tried just for the sake of it, but it locked up the computer even at a 1mhz overclock, hopefully someone else has an idea.

---

### Post by themattbeballin on 2009-09-08
I'll be ordering a laptop that will smoke my desktop graphics sometime soon anyway. so I guess I will be a Windows victim until then.

---

