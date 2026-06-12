---
title: "Hardware changes not captured by OS"
date: 2005-11-22
forum: General Help
---

### Post by EyeMWing on 2005-11-22
This applies both to hotplug (i.e. USB thumbdrives) and coldplug devices.

I'll add any of these devices to the system, and the Ubuntu will absolutely ignore them. They work and are compatible, because if I actually reinstall ubuntu, setup detects and configures it all.

I've tested:
- Adding new HDDs
- Adding new NICs
- USB devices of various descriptions
- Video cards (causes a nasty X crash)

As this system is tasked as a development server, and it's role is variable, hardware changes routinely reinstalling the OS is... Godawful inconvenient.

So, where do I go from here? I'm holding off on starting my work all over again in hopes that there's something that can be done to fix this.

Hardware is:
Dual P3 1.0
Intel Serverworks chipset
2gb RAM
5x 10kRPM HDDs on Adaptec AIC7880
Various NICs (3c905's, RTL8139's, some Intel stuff)
ATI Rage 128 Pro

DMESG agrees with me. Only hardware in there is the stuff that was present at setup.

Problems with this system run a lot deeper than I originally suspected. In DMESG, I note that it detects both CPUs, and then decides to ignore one because the "limit of 1 has been reached"

I guess it's time to port this project to Win2k3.

---

