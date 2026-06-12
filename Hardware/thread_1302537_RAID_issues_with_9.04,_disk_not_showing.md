---
title: "RAID issues with 9.04, disk not showing"
date: 2009-10-27
forum: Hardware
---

### Post by starbase1 on 2009-10-27
Hello All,
This on behalf of someone I am trying to help with getting Ubuntu installed.

Ubuntu 9.04 comes up nicely from the live CD, but it seems it cannot detect his hard drives, theres nothing under locations / computer. (It can see USB sticks, so it is working).


It's a RAID setup, and the device shows up under device manager as:

INTEL (IR) ICH8R (lots of numbers) DO SATA RAID CONTROLLER

Are RAID arrays often a problem for Ubuntu? Is there a recommended way forward? It's clearly going to be tricky to install to an invisible disk!

---

### Post by paul8472 on 2009-10-27
When I moved from Win to Linux I ended up getting rid of RAID because it was just too much hassle.  There is support using a module called "dmraid" (I think) but I could never get it to co-operate.

I think the fact that I used to use the drives in a RAID configuration is causing problems now with 9.10 RC as it thinks my drives are still in a RAID configuration.

Given that 9.10 is so quick to assume my drives are RAID maybe you'll have more luck with your friend's machine using the 9.10 installer!  9.10 is due out this Thursday (although a release candidate is available now if you want to check what happens in advance of then).

---

