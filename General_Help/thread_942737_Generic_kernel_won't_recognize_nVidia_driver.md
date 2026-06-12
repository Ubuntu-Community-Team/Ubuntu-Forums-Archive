---
title: "Generic kernel won't recognize nVidia driver"
date: 2008-10-09
forum: General Help
---

### Post by demios on 2008-10-09
So I installed the rt kernel with the ubuntu-studio suite, I think, and everything works ... passably well there. However, reading up on this I found that the generic kernel is supposed to work better for everything not audio-production related, so I booted there and it won't let me use the propriety driver for my nVidia GeForce 8 card -- though it recognizes the card. 

On boot it says I'm in Low Graphics mode, and that I have to configure the driver myself, so I opened the configure box and none of the changes I make stick -- I can browse through the lists of drivers and cards, but when I select one, it'll stay at the one that it started as, which is plug and play I think.

then I let it finish booting, and log in and such, go to the Hardware Drivers menu, and it says there are no proprietary drivers in or available for use -- though when I'm booted with the rt kernel, it lists the nVidia driver as in use.

There is probably an easy fix for this (I hope) that I just don't know. Any help is appreciated. I'll jot down the exact kernel names next time I reboot, but they're probably just the latest stable ones, I don't mess around with that kinda stuff.

---

### Post by LowSky on 2008-10-09
Have you tired using EnvyNG to install the drivers?
I believe it is now availible from the repos, and Add/Remove

---

### Post by demios on 2008-10-09
I'll try that. the name is ironic.

---

### Post by Nubicles on 2008-11-04
I had the same problem: installed the rt kernel, worked fine, booting the generic kernel broke my drivers.  Using EnvyNG fixed it.

---

