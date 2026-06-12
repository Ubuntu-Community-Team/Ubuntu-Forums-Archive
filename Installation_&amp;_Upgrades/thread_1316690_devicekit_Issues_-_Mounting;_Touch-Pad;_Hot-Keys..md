---
title: "devicekit Issues - Mounting; Touch-Pad; Hot-Keys."
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by proxess on 2009-11-06
I'm having a few issues due to the replacement of HAL with devicekit. I'm hoping someone can help me out with the issues.

1 - Mounting Partitions
1.1 - Start up
      I have partitions on my internal hard drive that don't mount at start up. When I do mount them, they also require password. I'd prefer the partitions be mounted at start up. On Jaunty, the partitions wouldn't mount at start up, but wouldn't request password.

1.2 - Suspend and external hard drive
      When I start up my laptop, my external hard drive mounts automatically. When I come from a suspend, my laptop re-mounts my internal hard drive's partitions, but it doesn't even detect my external hard drive, I have to unplug and plug it back in. On Jaunty, suspending the laptop would make the external hard drive switch off the plates and retract the needle, it also does that in Karmic, but when coming back from suspension, Jaunty would reboot the external hard drive and mount the partitions, Karmic doesn't.

2 - Touch-pad and Laptop Hot-Keys
    Pretty much all of my laptop's hot-keys work, for the exception of the disable touch-pad hot-hey. I have SHMConfig enabled in xorg.conf from Jaunty (I upgraded), but it makes no difference. I tried installing an applet for controlling the touch-pad (not the solution I'm looking for tho) but all I got was a segmentation fault.


My laptop is an Asus Z53Jr, which has the F3Jr motherboard, specifications are on my signature.

---

### Post by brokenthorn on 2010-08-17
I think this is pretty much a known issue.
DeviceKit brakes TouchPad detection on some hardware. Mine included. Check out bug [https://bugs.launchpad.net/bugs/550625](https://bugs.launchpad.net/bugs/550625)

---

