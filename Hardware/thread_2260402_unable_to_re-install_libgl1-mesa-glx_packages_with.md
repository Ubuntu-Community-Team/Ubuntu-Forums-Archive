---
title: "unable to re-install libgl1-mesa-glx packages without errors"
date: 2015-01-11
forum: Hardware
---

### Post by Handssolow on 2015-01-11
I want to install the current AMD Catalyst Omega (14.12) Driver to use with our HD7950 graphics card. There's already a well recognised bug and workaround by others because there's a conflict over libopencl1 which 14.12 says it needs and Wine (and Play on Linux) doesn't like. Looking for a solution to my failures to install the latest recommended AMD driver, I decide to re-install libgl1-mesa-glx packages in Synaptic and receive a similar error message in the terminal to when I attempt to install the AMD driver.

update-alternatives: warning: forcing reinstallation of alternative /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken

Not only can I not install the latest AMD driver, I am unable to re-install the libgl1-mesa-glx packages because of some broken link message. How might this matter be addressed?

Things are not helped by AMD stating that a requirement to install their latest driver depends on having XFree86-Mesa-libGL and XFree86-libs packages installed. What's that all about too?

---

