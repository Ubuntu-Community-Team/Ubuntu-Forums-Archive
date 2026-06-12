---
title: "Help fixing X after a video card upgrade"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by ControllerSphere on 2008-01-10
I just upgraded my desktop from a nVidia 7800GT to an 8800GT. After rebooting, the X server can't start because it can't find any displays, so it takes me to the shell. I tried uninstalling the nvidia-glx and nvidia-glx-common packages and reinstalling them, thinking that it was a configuration problem, but it didn't help, I also tried running nvidia-xconfig and nvidia-glx-config, with no change. I'm not really sure what to do next. Any suggestions?

The machine is a Core 2 Duo E6400 on an Asus P5B-VM board with 2 gigs of RAM running Ubuntu 7.10 i386. I'm also thinking about installing 7.10 x64 on it if I can't get X fixed,  but the liveCD boots to a blank screen even in safe graphics mode.

---

### Post by overdrank on 2008-01-12
> **ControllerSphere said:**
> I just upgraded my desktop from a nVidia 7800GT to an 8800GT. After rebooting, the X server can't start because it can't find any displays, so it takes me to the shell. I tried uninstalling the nvidia-glx and nvidia-glx-common packages and reinstalling them, thinking that it was a configuration problem, but it didn't help, I also tried running nvidia-xconfig and nvidia-glx-config, with no change. I'm not really sure what to do next. Any suggestions?

The machine is a Core 2 Duo E6400 on an Asus P5B-VM board with 2 gigs of RAM running Ubuntu 7.10 i386. I'm also thinking about installing 7.10 x64 on it if I can't get X fixed,  but the liveCD boots to a blank screen even in safe graphics mode.

HI and welcome, I believe with that model should be nvidia-glx-new. Are you able to get to any GUI (desktop) you may try and reconfigure your xorg in recovery mode. Recovery mode is usually the second choice in the grub.

---

### Post by Yellow Pasque on 2008-01-12
> I'm also thinking about installing 7.10 x64 on it if I can't get X fixed, but the liveCD boots to a blank screen even in safe graphics mode.
You'll need to use the AMD64 Alternate install CD.

Also, have you tried installing drivers from nvidia's site?

---

