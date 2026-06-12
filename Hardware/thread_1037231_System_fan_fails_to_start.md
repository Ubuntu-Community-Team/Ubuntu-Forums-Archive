---
title: "System fan fails to start"
date: 2009-01-11
forum: Hardware
---

### Post by fela on 2009-01-11
First off: I'm not entirely sure that this is a Ubuntu bug, it could be a bug with my hardware after all.

When I boot my machine the fan works, until the POST finishes and it starts to boot to the GRUB menu. When it says loading the grub menu, the fan stops and I can't restart it by giving the blades a shove manually. I have to boot into Ubuntu, start something resource intensive then start the fan manually. NOTE: even if I start something intensive like cpuburn (or loads of applications at once), it still doesn't start the fan until I give the blades a push. This leads me to believe that my system's lifetime is being compromised by a bug. Do you think it likely that it's related to Ubuntu? I really don't want to install Windows on my system just to test it.

Soon I'll boot a KNOPPIX live flash drive and see if it goes away. If it doesn't, then it could still be a Linux based bug but not Ubuntu in particular.

At first I thought that it wasn't starting because it was idle pretty much and not generating much heat. This was backed up by the fact that, while the computer was idle, I couldn't start the fans manually. But the fact that even running cpuburn didn't start the fans, and instead the CPU temps went right up to the early 50s for each core (dual core). Well that's according to the panel temperature applet, which is known to report temps such as -2 degrees C, so I don't know if I should believe that.

---

