---
title: "CDRom acting up"
date: 2010-03-10
forum: Hardware
---

### Post by Sumo74 on 2010-03-10
I am running Ubuntu 10.04, on an Acer Aspire 5810TZ. The problem is every time I blank a DVD or CD, I can not get it to remount and allow me to add things back to it. This has happened a lot and and I am running through everyone of my DVD-RW and CD-RW, just to burn some things I need (Trying to install some new distros to try out all the flavors of Linux).

This is the dmesg | tail output:

[   45.485555] cfg80211: Disabling channel 2467 MHz on phy0 due to Country IE
[   45.485557] cfg80211: Disabling channel 2472 MHz on phy0 due to Country IE
[   45.485560] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[   45.485566] cfg80211: Current regulatory domain updated by AP to: US
[   45.485568]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   45.485572]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   56.432033] wlan0: no IPv6 routers present
[  140.483196] UDF-fs: No anchor found
[  140.483202] UDF-fs: No partition found (1)
[  142.250820] ISOFS: Unable to identify CD-ROM format.

I am not for sure what is happening? Also my Pardus Linux distro won't boot because of an fs error, so it's something to do with all this crap (I think that might be because it is trying to boot from a boot image off the DVD, I haven't tested it to find out, but I can take a good guess and say so.)

Hopefully you all can help out me here. I don't want to run through all my ReWriteables, because that kind of defeats the purpose.

Edit: Some more info. No program can eject the CDROM, I either have to manually eject it (ejectcdrom in terminal) or restart the computer, which in the splash screen as the computer is running it's term commands, it ejects it out. Figured that little tidbit might help.

---

