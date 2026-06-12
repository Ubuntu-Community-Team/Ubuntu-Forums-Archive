---
title: "Using A Laptop with Multiple Different External Displays"
date: 2008-07-17
forum: Hardware
---

### Post by SnowflakeRV7 on 2008-07-17
Okay, so this is something that should be trivial but isn't.

First off, my computer:  I've got a Dell XPS 1330 (non-Ubuntu version, that i've Ubuntu-ized, 8.04 with all updates applied).  4G RAM, 160G drive, Bluetooth, Intel Wireless G, nVidia 8400 graphics.

I have installed the nVidia restricted driver, and the nVidia settings utility.  With those, I can control the laptop screen, and any of:

Viewsonic N4285P - 42" LCD TV, at 1920x1200 (max) or 1650x1080 (native) resolutions, over HDMI *or* VGA.  No problems.

Viewsonic VP201s - 20" LCD monitor, at 1600x1200, over VGA.  No problems.

Dell 2007FP - 20" LCD monitor, at 1600x1200, over VGA.  No problems.

The problem is that I have to hack my X11.conf file every time I change from one of these external monitors to another.  This is, understandably, a royal pain in the ****.  I use my laptop at work (Dell LCD), take it home and plug it into my KVM (Viewsonic LCD) and occasionally use it as a media PC to play movies (Viewsonic HDTV).

My solution so far is to leave my conf file set for the TV, because that makes it simplest when I want to watch movies (and my wife doesn't see me hacking files every time we do, so she doesn't think that Linux is a bunch of hacks that no normal person could ever use).

Obviously the laptop can find out what displays are connected.  And I can provide the settings it needs to use when it connects to each monitor (even if I have to go through a manual setup once to figure out what the optimal settings are).  So what do I need to do to make it detect the displays connected during bootup, and choose the appropriate conf file to boot from?

Any help appreciated...

---

