---
title: "Horrible experience with monitor without EDID"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by udippel on 2009-04-29
Firstly: Thanks to a really great 9.04! It runs on my desktop at office and home; as well as on my Acer Aspire One; beautifully!

I had a harrowing experience with my office desktop, though, when I plugged my high-end CRT IBM P260 instead of the cheap monitor used for install.
It would start - and do nothing. No keyboard, no mouse, low resolution. After a forced reboot ('Reset'-button), all I would get was a black, dead screen. Also, all recovery options would not make any difference, neither 'fix x', nor even going to root and nvidia-xconfig. All would result in a black screen and a number of pressing the hard Reset. No Xorg, no Xorg -configure.
The last and only resort: plug back that cheapo install monitor, for which another nvidia-xconfig was needed. Then I saved the xorg.conf there, plugged my IBM P260 after a restart, and finally I could work up my way by editing that xorg.conf, with Horiz (30-121) Vert (50-160), finally metamode to 1600x1200, with intermediate reboots for testing, and now I am at the usual 1600x1200 85 Hz. And the keyboard layout is still wrong.

Long story, short end: I guess Ubuntu/Xorg needs to better cater for situations when the monitor cannot be probed. There seems to be no proper fallback in case of something like

(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 TurboCache(TM) (NV44) at PCI:2:0:0
(II) NVIDIA(0):     (GPU-0)

(actually, the 6200 is there only, because the NVIDIA-driver is broken for IGP 8300, but that's not a story for ubuntu forums).

That's a complete show stopper for anyone with less experience when plugging the 'wrong' monitor! Somehow I wonder if this is worth a bug report?

Uwe

---

### Post by dandnsmith on 2009-04-29
An interesting tale - reminds me that I saw a post elsewhere which was asking for details of a reasonably cheap monitor which did do the EDID thing.

Any change such as this has the potential to render the system unusable, as the initial install will be presumed to set all necessary parameters - a similar situation with W**** will also cause problems under appropriate circs.

What is needed is an easy way of getting to the remedy, as it isn't really a bug (more of a feature!), which I think would be the dpkg-reconfigure in this case.

---

### Post by udippel on 2009-04-29
> **dandnsmith said:**
> 
What is needed is an easy way of getting to the remedy, as it isn't really a bug (more of a feature!), which I think would be the dpkg-reconfigure in this case.

Are you sure? I for one was thinking that the 'recovery-mode' option to 'fix x' would do exactly that. Not?

Also, one might think that a missing EDID-info would be replaced by one from a dummy monitor; something like 800x600, 60 Hz, us keyboard (if it really can't detect it properly like here). Don't let the user sit with a black screen; that's too scary for 99%. Pop up an info that the monitor could not be detected, and therefore the image is screwed. Point to a method to solve the problem; excpet of 'vi /etc/X11/xorg.conf'. There must be a better method.

Uwe

---

### Post by dandnsmith on 2009-05-02
I agree, but there doesn't seem to be an existing 'dig you out of a hole' which is invoked automatically.

One problem is that the system isn't looking for (and may not get) an error indication which corresponds to the 'out-of-range' condition a monitor will flag up - it's all built for use with monitors which are 'sensible'.

In older redhat releases, I seem to recall that everything was done in the install via command line and scripts which would ask for confirmation that things were OK - now it assumed that you have to use a GUI.

---

