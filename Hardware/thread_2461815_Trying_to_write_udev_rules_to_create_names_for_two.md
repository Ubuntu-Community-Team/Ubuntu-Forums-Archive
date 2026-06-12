---
title: "Trying to write udev rules to create names for two identical pieces of hardware"
date: 2021-05-07
forum: Hardware
---

### Post by le_jawa on 2021-05-07
I've got a PC to which I am connecting two identical Serial-USB adapters.  After several reboots, I started to notice that computer was very inconsistent in applying devices names.  Sometimes the one on the left gets the name ttyUSB0 and the one on the right gets ttyUSB1, and sometimes it's the opposite.

The only identifiers I have that are unique are ones related to the path, KERNEL and KERNELS being the easiest to work with.  I've already noticed that udev won't let me use the ttyUSB0/1 names, so I have to use other names or symlinks, but I still can't get seem to get udev to identify the devices consistently.

Any advice on how to fix the consistency issue (with the ttyUSB names or otherwise) would be greatly appreciated.  This one's got me stumped so far.

---

