---
title: "Slow performance on Asus X43U Laptop (AMD E-350, Ubuntu 12.04)"
date: 2012-07-19
forum: Hardware
---

### Post by Smokin Whale on 2012-07-19
Hey guys,

I picked up a cheap laptop the other day for browsing/email and videos. It came with Windows 7, but I perfer Ubuntu 12.04. I loaded it on and everything seems to work out of the box, but graphics performance in particular is pretty bad. It's an [Asus X43U]("http://in.asus.com/Notebooks/Versatile_Performance/X43U/").

It's based on the AMD Fusion E-350 APU and has a 1.6ghz Dual Core Brazos Processor with a Radeon HD6310. Using Gnome Shell and navigating around the interface is quite sluggish. In addition, CPU usage is quite high most of the time and 1080p playback is impossible (even 720p isn't perfect). I suspect is is related to the GPU where the CPU is forced to do most of the graphics rendering for some reason, however installing the proprietary drivers via the Ubuntu driver manager doesn't lead to any performance enhancement.

Anyone played with the AMD Fusion E-350 under Ubuntu 12.04? Or even better, has an Asus X43U? Suggestions on improving performance would be greatly appreciated! Surely a new laptop should fly with Ubuntu.

---

### Post by Smokin Whale on 2012-07-21
Forgot to mention - I threw Windows 7 x64 on there and things are much smoother, and 1080p playback is a breeze for it. Perhaps I should try 64bit Ubuntu?

---

### Post by Smokin Whale on 2012-08-15
Okay, so I've tried 64bit Ubuntu and the results are slightly better, although still totally unusable for HD video. CPU usage skyrockets every time, and it's clear that video decoding simple ins't happening with out of the box or third-party drivers and configurations on Ubuntu 12.04 32/64bit.

Any ideas to get this going? Otherwise I'm just going to have to go back to Windows, which is a damn shame.

Edit: Appears to be a video acceleration issue. Will continue to test. Has anyone else got a system running on the Fusion E350 platform?

---

### Post by Smokin Whale on 2012-08-22
Well, no help here, and after trying loads of different solutions, I'm done. 32 and 64bit Ubuntu video acceleration on the AMD E350 and Radeon HD6310 is just a no-go. Switching back to Windows. Performance is shocking on Ubuntu. I've also noticed this across quite a few different PCs with Ubuntu 12.04 with AMD GPUs and older Intel/Nvidia GPUs. How hard can be it be get drivers that work? I swear it's the number 1 issue from Ubuntu at the moment. Everything else is great, but unless you have a GPU that place nice, it sucks.

---

### Post by mpolat85 on 2012-09-04
I got an Asus A53Z with AMD A6 processor and Radeon HD6520 graphics and i have the same problem whichj drives me crazy. I have this problem under windows as well. It desn't work with 1080p HD videos on-line. Did you have any solution for that?

---

