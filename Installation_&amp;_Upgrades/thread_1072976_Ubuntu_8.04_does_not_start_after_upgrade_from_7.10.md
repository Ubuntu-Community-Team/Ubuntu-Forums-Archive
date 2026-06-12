---
title: "Ubuntu 8.04 does not start after upgrade from 7.10 and Nvidia driver installation"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by notexactly on 2009-02-17
My computer running Ubuntu 8.04 LTS now does not start up completely. I brought it upstairs earlier and hooked it up to the network. It was then running 7.10 and it asked if I wanted to upgrade to 8.04 LTS. I performed the upgrade and it restarted fine. A bubble appeared saying that restricted drivers were available. I clicked on the icon and it turned out to be an Nvidia graphics card driver. I installed this and restarted. It got to the splash screen with the orange progress bar, and then the screen went black when this was done. It did not respond to any input after this.

I have tried telling GRUB to boot in recovery mode, but the same thing happens (of course, it shows text instead of the progress bar). I did this two times. The first time I tried telling it to continue booting normally, and the second time to fix broken packages. It reported no errors with packages.

I'm pretty sure the Nvidia driver is at fault, because the machine worked fine before I installed it and it was the only thing I have installed since then. Any way to fix this? I mean, to remove the Nvidia video card driver?

SOLVED: In case anyone else has this problem, I found a that the solution was to boot into recovery mode, and choose xfix. Thanks overdrank!

---

