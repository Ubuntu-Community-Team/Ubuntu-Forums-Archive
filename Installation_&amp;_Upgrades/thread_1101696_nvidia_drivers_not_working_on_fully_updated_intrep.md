---
title: "nvidia drivers not working on fully updated intrepid..."
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by Space Cowboy on 2009-03-20
After fresh installing intrepid on my laptop this morning (not an upgrade), I've gotten just about everything working on it, but I'm still having an issue with the nvidia graphics.

I figured it might be fixed if I just updated, so I installed all the updates, and then enabled the nvidia accelerated graphics driver v180, and as soon as I reboot I get an error telling me that my hardware can't be detected correctly, that I have to configure these myself and that it needs to run in low-graphics mode, with an option to reconfigure graphics or troubleshoot the error.

I know the hardware is a nvidia graphics/mobo/eth combo "nvidia GeForce 7150m/nForce 630m" I'm not sure what to do with them though, and everything worked fine on Ubuntu 8.04

Eventually through searching I found "EnvyNG" got it through synaptic, and ran it, choosing at first the 180, no success there. Just to see if it would work I tried installing through EnvyNG the 177 version of the nvidia drivers, on reboot and same error it seems.

I saved the startup error log and the xorg log, I don't really understand them though. I notice at the bottom of the startup error log compatible NVIDIA X driver not found. Anyone know whats up? Should I just go back to 8.04? Any help is appreciated.

---

### Post by lemming465 on 2009-03-21
Either back to 8.04 or perhaps forward to the not-yet released 9.04 (I'm typing this from 9.04 alpha 6 :-)  A lot of X stuff changed between 8.04 and 8.10 and not all the dust has settled yet.

---

