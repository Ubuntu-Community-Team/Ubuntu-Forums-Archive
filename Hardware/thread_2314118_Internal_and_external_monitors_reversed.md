---
title: "Internal and external monitors reversed"
date: 2016-02-18
forum: Hardware
---

### Post by mfox on 2016-02-18
I am running Ubuntu 15.10 on a 2012 iMac with an external Dell monitor attached and attempting to control the monitor setup with the Nvidia driver version 352.63 settings. I don't think this is relevant, but just in case, the internal monitor has 1920x1080 resolution; the external has 1680 x 1050 resolution. The X Server Nvidia settings app gives me the opportunity to select which monitor is the primary display for the x-screen, and for this I select the internal monitor. But this doesn't seem to matter; when I start up the computer it always defaults to the external monitor for initial login and the window location for any app I start up (until I move it over to the other monitor). I looked at both the xorg.conf settings and the output of xrandr -q (both attached), and the external monitor is referred to as "DP-1" and the internal as "DP-2".  The xrandr output also refers to DP2 as the primary, but it isn't, at least not until I reopen the X Server Nvidia settings app after startup. The xorg.conf file, section Monitor, seems to refer to the internal monitor as "Monitor0" if I am interpreting the output correctly, and "Device0" as the nvidia graphics card in my Mac. I am not an advanced user and I don't know how to manipulate the monitor settings other than through the GUI X Server Nvidia settings, and this doesn't seem to do any good as far as making the internal monitor the primary monitor. I would really appreciate any advice as to how I can reverse this.

Incidentally, if I log out and log back in, both monitors go blank and the only way to recover is to reboot. Reboot always turns on both monitors, but with the wrong one (the external) as the primary.

---

