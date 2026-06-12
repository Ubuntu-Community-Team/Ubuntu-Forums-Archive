---
title: "Determining which program/driver version is installed"
date: 2008-11-14
forum: General Help
---

### Post by R3M3 on 2008-11-14
Is there any way to easily find out when the snapshot of a program was taken (which external version was used) to make the Ubuntu package?

Note that I'm looking for the external version numbers used by the original program maintainers (or snapshot date from the repository), not the internal Ubuntu version numbers reported by Synaptic, etc. For example, the internal version number of the most recent kernel package is 2.6.27-7.16 as reported by Synaptic, yet the most recent kernel version listed on kernel.org is 2.6.27.6. I would want to know what the kernel.org version number would be for the Ubuntu 2.6.27-7.16 kernel. (But in a general sense, not just the kernel.)

The reason I want to know is that I'm trying to troubleshoot a hardware issue, which the original driver maintainers think might be fixed in a recent driver update. I want to determine which version of the driver I'm actually running. (In case it matters, it's the v4l-dvb system.) This is complicated by the fact that, as best I can tell, the driver modules are lumped into the linux-image-2.6.27-generic package, along with the kernel and a host of other drivers.

---

