---
title: "Are drivers controlled by the kernel?"
date: 2014-09-08
forum: Hardware
---

### Post by newb85 on 2014-09-08
First, I'll start with this: I've been talking with/trying to help a friend who's just getting his feet wet in Linux, and it's brought to my attention my limited understanding in an area where I've never had trouble.  I've never actually sat at his machine, and probably won't.

After building his own machine (something he's done before), he tested live media of Ubuntu, Lubuntu, and Mint.  The variety of his results baffles me.  The first problem he experienced was that Ubuntu wouldn't work with his network card unless he went into the BIOS and switched something, which then disabled some of his USB ports.  He said his online search revealed it's a common Linux problem for his mother board.  I wasn't terribly surprised by this until he told me that when he tested Lubuntu, it actually worked.

Moreover, he said that he experienced some graphics issues in Ubuntu, but in Mint, he doesn't.  He said Ubuntu was using driver version 515 and Mint 516.

I've always been under the impression that drivers are actually in the kernel.  And I've always been under the impression that Ubuntu and Lubuntu (and I would assume Mint) start with the same kernel and have the same alternatives available.  Is this not correct?  If the kernel that works with his hardware is available in Lubuntu, shouldn't it be possible to use it in Ubuntu?  If the 516 drivers are available in Mint, shouldn't they be available in Ubuntu?

I would appreciate if someone could un-muddy the waters for me.

---

### Post by grahammechanical on 2014-09-08
First, it all depends on whether Ubuntu and Lubuntu are the same release as to whether one has a later Linux kernel than the other. As for Linux Mint, I have no idea and I have know wish to find out.

Kernel modules are built into the kernel at installation time. Ubuntu does not install proprietary software like video drivers unless we tick the box "Install Third Party Software" at the start of the installation. Ubuntu does not have the latest untested proprietary video drivers. The Ubuntu developers aim for stability, especially with Long Term Support releases. Every six months or so an LTS release will receive a point release. Ubuntu 14.04 has just become 14.04.1. This release has newer Linux kernels and hardware support. This is how a Ubuntu LTS release stays current with hardware developments.

Updates to Ubuntu after the version has been released are called Stable Release Updates (SRU) and there are strict rules controlling whether the release gets an update of any package,

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

The chart at the bottom of this wiki page will show you the scheduled point releases for 14.04

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Regards.

---

### Post by newb85 on 2014-09-09
Thanks for the reply.  His Ubuntu and Lubuntu tests were both 14.04, and I believe they were both downloaded before 14.04.1 was released. That's what baffles me. They act like they have different drivers when they shouldn't.

---

