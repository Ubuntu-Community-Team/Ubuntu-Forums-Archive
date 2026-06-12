---
title: "Poor performance w. P4 HT 3GHz, 4Gb, ATI HD 2400 Pro"
date: 2010-05-17
forum: Hardware
---

### Post by mikrogroove on 2010-05-17
Hi all, 

I would have thought I have a reasonably capable system but either something is wrong with my setup or Ubuntu is a dog. My laptop running XP outperforms my desktop Ubuntu system by at least a factor 2 to 1 - and that's even when the laptop CPU is locked to 600MHz! 

I'm running Ubuntu Server 9.10, no Compiz and all effects etc turned off. Yet even typing this text I notice a slight lag on each keypress! Scrolling large pictures in Gimp is a pain with banding and tearing, basically everything is just sloooooow. I'm farily new to Linux (3 months now) and I don't know where to start to figure out what the problem might be. I have the Catalyst ATI drivers installed but I cannot enable accelerated video playback (if I do I just get a black square where the video should be) so full screen video is like a slideshow (practically unwatchable even in a window). Running a just few programs (say Nautilus + Firefox + Gimp + Pidgin) CPU utilisation hovers between 20% and 50% on both cores. The CPU fan (temperature controlled) regularly spins up like a jet engine (never did this with Windows), even just opening a folder with many files in with Nautilus will set it off and opening a folder with photos or videos takes forever (rendering the thumbnails). 200+ files and I might as well go make coffee before the list is complete. Scrolling webpages (even ones without Flash) is sluggish and jittery. Etc, etc, etc. All these things work perfectly on my XP laptop despite a vastly inferior specification! 

Does anyone have any tips on what I can look at to start to figure out what is wrong? Are there commands I can run to check that CPU, chipset, SATA controller etc are correctly configured and have the right drivers? Benchmarking? Do I need to compile my own kernel perhaps? If I cannot improve the performance of this system I will have no choice but to go back to Windows :( It is excruciating to use the machine, and I work on it 10+ hours a day. Any helpful suggestions greatly appreciated!

---

### Post by khelben1979 on 2010-05-17
How much RAM? Is it 4 GB as you wrote above?

I am not sure why your system get's so slow (yet). The solution might be to go for another version of Ubuntu which uses another Linux kernel. Have you tried this?

---

### Post by mikrogroove on 2010-05-17
> **khelben1979 said:**
> How much RAM? Is it 4 GB as you wrote above?

Yes, 4GB of RAM, although only a little over 3GB of that is usable of course. I think the performance issues I have are related to the graphics drivers, specifically 2D acceleration not working (so the CPU has to do all the work). I have tried to figure out what may be wrong but all settings etc do seem to be correct and Catalyst Control Center doesn't report any issues.

---

