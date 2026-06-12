---
title: "Recent nvidia driver update breaks Sony Viao"
date: 2008-06-15
forum: Hardware
---

### Post by sc0jack on 2008-06-15
Hi all,

Summary: After automatic update yesterday of NVIDIA drivers via update-manager, neither envy nor standard nvidia drivers will load. Stuck on low-res.

Sitrep:
Platform: Sony Viao VGN-S4M laptop
OS:       Ubuntu 8.04 Hardy (2.6.24-19-generic)
GFX:      Nvidia Go 6200/128meg

So update-manager ran yesterday, updating various bits and bobs, including both the envy nvidia drivers I was running with, and also the standard Xorg version. On reboot, it looked like the X system tried to start up three times, bombing out to command line each time. Then, X finally started up and a dialog came up saying that I was stuck in low-res mode and if I wanted to get higher res I had to configure it.

I hit configure, and went to the hardware tab. I manually selected the "nvidia" driver from the list, and went back to the screen res tab. The only resolutions available to me were 800x600 and 640x480. The screen supports up to 1280x800 widescreen, but this was not offered as an available resolution.

I logged in and ran the envy client, and installed the new driver. Rebooted, and ended up at the same low-res, please configure dialog. Back to the desktop, and reinstalled the envy driver - same result. Next, I tried uninstalling the envy driver. On reboot this brought me back to the desktop ok, but in low-res using the Xorg driver. I went into hardware drivers app and enabled the Nvidia driver. Rebooted, and we're back to the low-res, please configure dialog.

No matter what I do, with either envy or the Xorg driver, neither driver appears to be able to detect my nvidia card. There are no definitions whatsoever for my Sony Viao laptop screen in the monitors section of the graphics settings (is there REALLY noone else running ubuntu on a Viao??) so I usually run with either Plug and play monitor, or LCD 1280x800.

There seems like little point in messing around with the Xorg.conf right now, since the nvidia driver seems completely incapable of detecting my Geforce GO 6200. Do any of you have any ideas what could be wrong? Right now it simply seems like the driver doesn't support my card, when it did the day before. This is the "new" driver, which all configuration routines say supports my card.

Sorry for the long-winded post, and apologies in advance if this is a duplicate of another thread. I didn't change anything, so it's doubly frustrating to get ham-strung by an automatic update.

Scott.

---

### Post by sc0jack on 2008-06-15
More info:

Hardware: NV43 [GeForce Go 6200/6400]

Nvidia software versions that appear to be installed (gathered by doing a search for "nvidia" from synaptic package manager):

envyng-core                                1.1.1ubuntu17
envyng-gtk                                 1.1.1ubuntu1
jockey-common                              0.3.3-0ubuntu8
jockey-gtk                                 0.3.3-0ubuntu8
linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.42
nvidia-glx-new                             169.12+2.6.24.500-500.24~envy
nvidia-kernel-common                       20051028+1ubuntu8
nvidia-settings                            1.0+20080304-0ubuntu1.1

When at the "low-res" dialog on boot up, setting the driver to "nvidia" and selecting my usual "LCD 1280x800" monitor definition, the test fails without displaying anything, so the card isn't being recognised at all...

Scott.

---

