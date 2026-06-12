---
title: "Dell Latitude E4310 Dual Monitors freezing"
date: 2010-06-09
forum: Hardware
---

### Post by kilativv on 2010-06-09
Hi,
I have installed Lucid on E4310 and everything works fine(except for a little quirk with intel sound) Now I'm trying to connect dual FullHD Dell screen via docking station DVI ports. First of all, if I boot the laptop while plugged into the dock, it just freezes as outlined below. If I first boot it and then plug into the dock, the following happens: in the System->Preferences->Monitor I can see 3 panels available: laptop LCD and two Dell monitors(those are off). However, when I try to disable e4310's panel and enable two Dell monitors, all screens just go blank and system completely freezes up. No SSH/Cltr+alt+bkspc/Cltr+alt+F1 possible. Also that is not a kernel panic as no keyboard lights are blinking. 

However everything works if I only enable the laptop's LCD and only one of the Dell monitors. I Have also tried disabling the laptop panel prior to enabling the second Dell monitor via **lxrandr** It allows me to completely disable the built-in panel(leaving just one DVI Dell running) but then as soon as I enable the second Dell, eveything just freezes the same way.

I'm attaching lshw output so the HW can be correctly identified. Oh, also, I'm running 64bit.

---

### Post by kilativv on 2010-06-09
Update:
So i thought that maybe 64 bit OS is the cause of the issue. So I booted the 32bit liveCD and voila - everything works. However, when I installed it onto the HD(32 bit version) the problem is back. Very strange.

---

### Post by lxg on 2010-06-24
I have the same issue. Dell E4310, when I plug in the VGA cable and open the "Display" tool, the machine freezes. :(

---

### Post by lxg on 2010-06-25
I found out some more:

- When I'm logged in from another machine, I can still interact with the E4310 – for a short while, until SSH also stops to work.

- Deactivating desktop effects via Appearance doesn't help.

- There are some related bugs in Launchpad, apparently concerning freezes on certain Intel chipsets and Dell machines when using gnome-display-properties or xrandr.

I also can confirm that managing dual screens works when the system is started from the Live CD. So what's the difference between Live CD and installed system?

---

### Post by kilativv on 2010-07-29
Yeah, I have all the exact symptoms. It freezes, but I'm still able to access it via SSH for a little bit.

Please comment on the bug that I opened: 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/591929](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/591929) 

Also I'm able to use just one external monitor if I enable it via lxrandr(or xrandr), so if you only have one, that might be useful for you.


I also tried running Fedora LiveCD and it seems to have the same issue.

---

### Post by kilativv on 2010-08-06
Looks like installing latest drm-intel kernel fixes this issue.

---

### Post by alecz20 on 2010-11-24
> **kilativv said:**
> Looks like installing latest drm-intel kernel fixes this issue.

How did you install these drivers?


I have the laptop and one external display.

If I want to enable both, so that the desktop extends to the other one, the system completely hangs with a black screen.


So again, how did you install the drivers?

Did you use the method at this link: [http://www.khattam.info/howto-install-latest-intel-drm-kernel-to-avoid-crashes-on-boards-with-intel-hd-graphics-2010-08-14.html](http://www.khattam.info/howto-install-latest-intel-drm-kernel-to-avoid-crashes-on-boards-with-intel-hd-graphics-2010-08-14.html)

---

