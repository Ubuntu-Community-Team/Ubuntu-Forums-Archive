---
title: "detecting second monitor ati"
date: 2009-04-17
forum: Hardware
---

### Post by bwm71 on 2009-04-17
I've had Ubuntu 8.04.2 running for a while and I just added a second monitor to my setup.  I'm running and ATI Radeon HD 3470 card with dual DVI outputs.  The problem is that there is no signal at all to my second monitor.  That is, the monitor goes into power save mode due to no signal.  Just like it's not plugged in to a video source.

I guess my question is about the order in which I should expect things to happen.  Clearly, since there is no signal to second monitor, the ATI Catalyst Control Center only show one monitor and my xorg.conf has only one monitor and screen section.

Should I expect a signal to this monitor even though Xorg may not yet be configured correctly?  I am using the proprietary fglrx driver. 

Thanks,
Brandon

---

### Post by bwm71 on 2009-04-24
Solved the problem.  I had a bad DP2DVI cable.  After switching this out, the second monitor came right up.

---

