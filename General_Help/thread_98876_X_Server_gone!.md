---
title: "X Server gone!"
date: 2005-12-04
forum: General Help
---

### Post by Kanephan on 2005-12-04
I screwed up :???: 

I was trying to get America's Army to run, and installed some new Nvidia drivers. Apparently they were the wrong ones, and now X Server can't start up.

How would I go about reverting?

EDIT:

This is the error:

ERror: API mismatch: the NVIDIA kernel module is version 1.0.7174, but this X module is version 1.0.7667. Please be sure taht your kernel module and all NVIDIA driver files have the same driver version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):  that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):   that the NVIDIA device files have been created properly.
(EE) NVIDIA(0):   Please consult the NVIDIA README for details
(EE) NVIDIA(0):   ***Aborting***
(EE) Screen(s) found, but none have a usable configuration.



I understand the problem, I just don't know what commands and where to go to fix them. I can't do this by myself with only the terminal to use. Help please!

---

### Post by Kanephan on 2005-12-04
I installed the old nvidia-glx-legacy drivers, and ubuntu started up fine.


Seems I solved my own problem. Go me.

---

