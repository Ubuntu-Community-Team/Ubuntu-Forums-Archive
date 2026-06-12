---
title: "xorg startup boot sequence"
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by TubaTodd on 2007-11-09
I've been having a recurring problem with my laptop (intel gma 950 video board) and external monitor setup. My external monitor is my main display and has a resolution of 1680x1050. When I boot into Ubuntu 7.10 (from the liveCD or from the Hard drive install on a different partition), I will occasionally get a pair of thin lines on my external monitor after x windows starts up. I've tried changing video drivers from the "intel" driver to the more stable "i810" driver, but the change has no effect. 

I read another post in this forum where someone said they were getting ugly stripes (worse than mine) on their screen when ever a particular service was loaded with(out) another service running prior to it. My question is, is there a way to view the startup sequence of x windows in my Ubuntu 7.04 install and my 7.10 install to figure out perhaps what the deal is? 

These lines are the ONLY thing keeping me from upgrading to 7.10. Any ideas would be GREATLY appreciated. Thanks

---

### Post by TubaTodd on 2007-11-09
bump

---

### Post by dabl on 2007-11-09
Yep.

There's a log file at /var/log/Xorg.0.log that shows the sequence.

:guitar:

---

### Post by TubaTodd on 2007-11-09
ok, suppose I do see something when comparing the Xorg.0.log files of a good boot and a "bad" boot and I find that the boot order of a couple services is different. What regulates the order in which the xorg services load? Is that purely the xorg.conf file or is there something else? Thanks

---

### Post by TubaTodd on 2007-11-10
Ok, here's what I did. I decided to boot from the 7.10 CD and copy the Xorg.0.log from a "good" boot and a "bad" (lines on the screen) boot. I compared them line by line. The 2 log files were almost identical. I've outlined the differences to see if this makes sense to anyone. To me, I just don't see anything glaring. Maybe one of you will. 

**Good**

(II) intel(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) intel(0): [drm] added 8192 byte SAREA at **0xf8bda000**
(II) intel(0): [drm] mapped SAREA **0xf8bda000 to 0xb7ba0000**
(II) intel(0): [drm] framebuffer handle = 0xc0040000
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): Unable to use TTM-based memory manager with DRM version 1.6

**Bad**

II) intel(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) intel(0): [drm] added 8192 byte SAREA at **0xf8c10000**
(II) intel(0): [drm] mapped SAREA **0xf8c10000 to 0xb7b3f000**
(II) intel(0): [drm] framebuffer handle = 0xc0040000
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): Unable to use TTM-based memory manager with DRM version 1.6

**Good**

(--) Synaptics Touchpad touchpad found
[b]ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?[/b]
SetClientVersion: 0 9
(II) intel(0): Output VGA connected

**Bad**

(--) Synaptics Touchpad touchpad found
SetClientVersion: 0 9
(II) intel(0): Output VGA connected

---

