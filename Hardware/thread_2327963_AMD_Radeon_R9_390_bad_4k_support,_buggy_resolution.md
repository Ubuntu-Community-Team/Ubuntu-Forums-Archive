---
title: "AMD Radeon R9 390 bad 4k support, buggy resolution changes etc."
date: 2016-06-16
forum: Hardware
---

### Post by lilleman2 on 2016-06-16
**EDIT:** After some help from the fantastic humans in #radeon@freenode, more exactly bnieuwenhuizen and vedranm, the issue was in fact the screen being set to DisplayPort 1.1 and not 1.2. When that change happened it worked like a charm with the open source radeon driver. Link to the solution: [http://ubuntuforums.org/showthread.php?t=2241888](http://ubuntuforums.org/showthread.php?t=2241888)

**EDIT2:** After using the system for a little while I noticed a flickering on the screen. Sometimes worse sometimes better.  Another fantastic human in #radeon@freenode, AUser solved this by running:

sudo sh -c "echo high > /sys/class/drm/card0/device/power_dpm_force_performance_level"

To make it stick after reboot, enter

KERNEL=="card0", SUBSYSTEM=="drm", DRIVERS=="radeon", ATTR{device/power_dpm_force_performance_level}="high"

into the file /etc/udev/rules.d/30-radeon-pm.conf (create it if it does not exist)


**Original post**:
Any help with resolving the issues described below is highly appreciated! If they can not be solved, let this post be a warning to others about buying this card (for now, before proper driver support)

I recently purchased this card instead of going with some top-of-the-line Nvidia card because of Nvidia being assholes to the open source world.

Before buying I googled quite a lot to get an idea about the support. Maybe my googling skills is crap, but I did not find much complaints. Mostly it was about games not running as fast as under Windows. I do not care about that, I code, watch movies and toss a lot of windows around on my desktop, thats it.

However, it seems the open software driver is not handling this card well. In 4k resolution I get very sluggish performance, in 30hz (my screen supports 4k@60hz). The whole feel of the desktop is as if it is running 100% software and not using any 2D hardware acceleration. When changing to a lower resolution the screen goes blank and the only thing I can do is reboot to get my sluggish 4k back.

This is a fresh install of Ubuntu 16.04 and I am very willing to flush my disk with other options to see if the problem can be resolved somehow.

I am going to try the Vulcan driver from AMD now... not being open source and requiring a large end user agreement I do not really see this as an option, but I have to try if it works at all.

A quick note about the AMD licence agreement: AMD is allowed by that agreement to send information about your system to AMD; "including the model of AMD graphics product, its device id, and other system information"... It says non-personal, but since they are sending it they get your IP and with the device id they can also track down your purchase.

Now I've tried installing the Vulcan driver. That renders a blank screen instead (screen identifies the black screen as 4k@30hz though).

---

