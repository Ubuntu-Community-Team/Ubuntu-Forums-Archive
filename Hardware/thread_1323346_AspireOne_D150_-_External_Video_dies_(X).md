---
title: "AspireOne D150 - External Video dies (X)"
date: 2009-11-11
forum: Hardware
---

### Post by jbeiter on 2009-11-11
I've been using the netbook remix 9.04 Jaunty on the Acer AspireOne. Everything works great but recently I started using an external monitor/keyboard.

At seemingly random times, the external video goes black. I can often toggle the built-in lcd to come back on using the Fn-screen key combo but nothing seems to fix the external video except a reboot.

I can do control-alt-F1 and character mode works, but trying to go back to X just gives a black screen. This happens on different monitors too.

Acer support is useless, once they hear I wiped mickysoft and loaded Ubuntu, they are done helping.

Any ideas? I'm not sure if this is hardware or software.

---

### Post by jbeiter on 2009-11-12
Nobody has seen this before?

The only error I see in Xorg.0 is:
xf86UnbindGARTMemory: unbind key 0

I try to kill X but only the laptop screen comes back. Reseating the external video cable doesn't do anything.

Just a Microsoft Salute works.

any help at all?

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

