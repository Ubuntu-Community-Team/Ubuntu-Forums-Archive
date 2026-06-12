---
title: "New Monitor .. Out of Range"
date: 2009-02-25
forum: Hardware
---

### Post by gambrjl on 2009-02-25
Got myself a new 26" monitor.. (it's BIG)

It came with a DVI -> HDMI cable and your standard VGA cable. Monitor has HDMI in and also VGA in. Computer has dual DVI out via a Gforce 8600 video card using the NVIDIA driver. I have a little adapter for the DVI to VGA when I use the VGA cable. When I plug in via VGA everything works like a dream.. 1920x1200 resolution at 60 Hz. When I plug in DVI->HDMI I instantly get an Out of Range message before Ubuntu even tries to start X. 

No BIOS message or boot up or anything

Tried booting of LiveCD.  Out of range.  It's not even getting to a point where it's using X and it's already out of range

---

### Post by gambrjl on 2009-02-26
Anyone have a clue??  I can't figure why the resolution and refresh would be different on bootup between a VGA connection and the DVI->HDMI

---

### Post by bvillegas on 2009-02-28
I am having the same problem.  Just had new monitor and I am getting OUT OF RANGE 35.5 KHz / 87 Hz error.

Error msg:

usplash: setting mode 1152 x 864 failed
usplash: using mode 1024 x 768
         check root = bootarg cat/proc/cmdline
         or missing modules, devices: cat/proc/modules ls / dev
ALERT! /dev/disk/by-uuid/1054562F54561834 does not exist.  
        Dropping to a shell!

How do I fix this?

---

