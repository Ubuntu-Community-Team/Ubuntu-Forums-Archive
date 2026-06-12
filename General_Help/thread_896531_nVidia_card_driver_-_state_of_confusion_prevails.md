---
title: "nVidia card driver - state of confusion prevails"
date: 2008-08-21
forum: General Help
---

### Post by Greasyfingers on 2008-08-21
I have an nVidia RIVA TNT2 Model64 graphics card, and am running Hardy. I've never bothered with anything to do wih graphics card drivers before - whatever Ubuntu sets up by default, it works OK-ish (general appearance is all I want - no fancy stuff, just a basic desktop, file and window management). But video playback is always a but lumpy - DVDs stutter a bit, as does YouTube, and Viddler is pretty well unwatchable - really just a series of still images. I've always assumed this is to do with an old and slow computer, but someone suggested it could be improved if I enabled the non-free restricted card driver.

So I went System -> Administration -> Harware Drivers and checked the Enable box for the 'NVIDIA accelerated graphics driver (legacy cards)'. This downloads a file, and then prompts for a computer restart, which then boots into low graphics mode, with a window appearing just before the desktop saying that the graphics card could not be detected, and asking me to configure it manually. No matter what I select from here, the only thing that gets me out of low graphics mode is selecting for a Generic VESA compliant card (which is presumably where I started from). From here, I seem to go round in a circle, and can never enable the driver for the card.

Similarly, if I go System -> Preferences -> Appearance -> Visual Effects selecting anything other than 'None' prompts to enable the driver and reboot, which again puts me into low graphics mode unable to get out of it without going back to the previous state.

I've backed up xorg.conf, and replacing this seems to be the way to get back to where I started, but I'm pretty confused by all this - what should I be achieving by enabling the driver, and how can I make it work?

---

