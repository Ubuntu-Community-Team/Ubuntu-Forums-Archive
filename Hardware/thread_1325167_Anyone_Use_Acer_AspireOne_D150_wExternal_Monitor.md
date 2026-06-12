---
title: "Anyone Use Acer AspireOne D150 w/External Monitor?"
date: 2009-11-13
forum: Hardware
---

### Post by jbeiter on 2009-11-13
I am having only one problem with the AspireOne D150 Netbook, using Jaunty 9.04 and the netbook remix. At seemingly random times, the external video will just black out. Re-seating the cable does nothing. Restarting X will not kick it back on. The built-in lcd does work though.

Rebooting seems to be the only thing that works at this point.

If restarting X (by killing it) does not get the monitor going again, does that mean it is a hardware problem? I tried re-detecting monitors and turning it on again via the System->Displays->admin tool but that didn't work either.

Acer won't talk to me since it was purchased with Windows XP and I wiped it and installed Ubuntu. I would really like to avoid loading windows up just to test it if I can find a software issue with the ubuntu setup.

any ideas for me?

---

### Post by jbeiter on 2009-11-13
may be due to an xorg bug. Put the following in my xorg.conf:

Section "Device"
 Identifier "Configured Video Device"
 Driver "intel"
# VideoRam 16384
# It turns off disabling pipa A by a driver after while.
# Its 100 % working workaround.
 Option "ForceEnablePipeA" "true"
 Option "ModeDebug" "yes"
 Option "FramebufferCompression" "off"
EndSection

as per this thread: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/257894]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/257894")

---

