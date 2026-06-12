---
title: "HP DV7T Microphone Port Not Working"
date: 2011-04-12
forum: Hardware
---

### Post by Lancelot59 on 2011-04-12
The front microphone port on the front of my laptop isn't working. I'm running a HP DV7T. It was working before, but I guess it stopped after I got backport snapshots of the ALSA drivers for this new version of the kernel. The internal microphones work.

I checked and nothing is muted, it just stops working when I plug a microphone into the slot. I've looked around and haven't found a solution. I modified the alsa-config file to use model=dv5t, which was a fix to get the bass speaker working.

---

