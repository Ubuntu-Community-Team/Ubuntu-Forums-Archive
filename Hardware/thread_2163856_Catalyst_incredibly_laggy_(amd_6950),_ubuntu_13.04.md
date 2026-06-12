---
title: "Catalyst incredibly laggy (amd 6950), ubuntu 13.04"
date: 2013-07-19
forum: Hardware
---

### Post by screaminj3sus on 2013-07-19
I installed ubuntu on my main desktop, I figured since most of the games I play a lot are now natively supported (CS:S, Dota 2, L4D2, TF2, killing floor etc..) it was time to finally ditch windows.

I have some big issues with the amd catalyst driver though. The video card is a 2gb AMD 6950. Running ubuntu 13.04 64-bit, using the catalyst driver from "fglrx-updates" which I assume is the newest. With the default OSS driver the unity desktop was butter smooth. Smooth animations, window movement, scrolling in firefox, and zero tearing, and surprisingly I could run CS:S just fine with no input lag or tearing (haven't tried newer source games yet though, don't know if they will be as smooth) (EDIT: l4d2 performance rather poor with oss driver, although its 'playable').

After installing the "faster" proprietary driver I experienced very noticeable lag and jitter all over. Scrolling was especially horrendous, smooth scrolling in firefox was basically not usable. Lots of video tearing and laggy scrolling.

I tried the following settings tweaks:

Disabling vsync in compiz, disabling vsync in catalyst. Result: Pretty smooth unity desktop, very smooth in games, but obviously massive tearing all over on the desktop and scrolling which I do not find acceptable.

Disabling vsync in compiz, enable tear-free desktop in catalyst. Result: No tearing, but super laggy scrolling, window movement, animations, and massive input lag in games.

Vsync enabled in compiz, tear-free disabled in catalyst (this is the default settings). No tearing moving windows, somewhat smooth animations, but laggy firefox scrolling and tearing when scrolling in firefox, good performance in games.

Is there anyway to properly configure this so I get no tearing and performance as smooth as with the OSS driver for unity?

---

### Post by Yellow Pasque on 2013-07-20
I would try the latest driver (Catalyst 13-6 beta). Your symptoms sound the same as the person in this thread: [http://ubuntuforums.org/showthread.php?t=2163722](http://ubuntuforums.org/showthread.php?t=2163722)

---

### Post by screaminj3sus on 2013-07-20
I installed 13.6 this morning (+ tried all those different configurations again), but the performance was the same. Also tried installing gnome-shell to see if it was just a problem with catalyst + unity, but gnome-shell had the exact same behavior. I was hoping AMD's linux drivers had improved from when I had last tried them in linux years ago, but they are still quite sub-par :(

Its so weird how their driver performs so much better in 3d applications than the OSS one, yet can barely handle something as simple as a composited desktop :/

---

### Post by homerhomer on 2013-07-30
Try this driver - [http://phoronix.com/forums/showthread.php?82591-(23-07-)-AMD-Catalyst%99-OpenGL-4-3-Beta-Driver](http://phoronix.com/forums/showthread.php?82591-(23-07-)-AMD-Catalyst%99-OpenGL-4-3-Beta-Driver)

---

