---
title: "Main monitor in TwinView setup dead after upgrade to 180.22"
date: 2009-01-17
forum: Hardware
---

### Post by cookiecaper on 2009-01-17
Hi all.

I don't use Ubuntu, but I want to put this before a larger forum than my relatively-small distro and nvNews. One day after upgrading to 180.22 stable, the first monitor in my TwinView setup is dead; it will display the image very quickly (~1 second) when you've just switched video modes, but the button turns red and the monitor goes to sleep immediately thereafter, although there is still signal output. I've switched DVI ports and checked the video card otherwise and those things seem to work fine (i.e., the different ports and the video card), though I have not yet gotten around to testing my faulty monitor on a wholly different machine.

I haven't tried regressing to 178.xx series yet, but I did try booting into Vista to no avail. It doesn't appear to be a problem with a stuck invalid refresh rate or some such because I can't seem to unstick it in any video mode, up to and including booting into Windows, and the monitor typically displays an "Out of Range" message when invalid modes are attempted.

I'm somewhat inclined to believe that this is a coincidental short circuit, as it doesn't seem driver-dependent (happens during POST and in Windows) and happens even when one presses the monitor's menu buttons, but I just want to ensure that it doesn't involve nVidia's latest release, and poll the community for similar reports (in case they had such problems and wrote them off as the same). Thanks for your time, everyone. : )

Specs:
EVGA nForce 6 NF68-SLi
Core 2 Duo E6600
GeForce 7900GTO

Monitor is identified by nvidia-settings as KET KT-201QE. It's ViewEra brand.

This is a sad day. Thanks for any and all help.

---

