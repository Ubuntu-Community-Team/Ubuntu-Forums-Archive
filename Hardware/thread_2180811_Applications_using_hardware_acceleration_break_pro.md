---
title: "Applications using hardware acceleration break proprietary GPU drivers"
date: 2013-10-14
forum: Hardware
---

### Post by boat2 on 2013-10-14
Or at least that's what I assume is happening. So the issue I got here is that whenever I've launched a game with wine or used vmware, games that run natively in openGL (i.e dota2) run very bad, pretty much just like they did on the FGLRX driver from "additional drivers". Until I've touched anything that's used the GPU everything runs fine. I'm using the "AMD Catalyst™ 13.4 Proprietary Linux x86 Display Driver" with a 7850 on Ubuntu 12.04 which should be installed properly. 

I'd appreciate some help on this. Thank you in advance.

---

### Post by QIII on 2013-10-14
Hello!

I'm afraid you may have some unrealistic expectations of Wine and virtualization.

With regard to performance under Wine, you will have to consult the database at WineHQ to check how your games run in Wine.  Not everything runs well. 

With an virtualization solution other than something like KVM (which is actually part of the Linux kernel) and something like SPICE to directly access the graphics hardware, the guest machine is not actually making contact with your GPU on "bare metal", but rather on a hardware abstraction layer provided by the virtualization software - there is software communication between the guest machine and the host's hardware and that is terribly slow and inefficient.  In general, the graphics performance of that virtual hardware is very poor and does not lend itself well to graphically intensive processes.  High end gaming is not really feasable at this point with things like VMWare and VirtualBox.

With virtualization, it doesn't matter much that the host has a proprietary driver with hardware acceleration.  The guest is using only very rudimentary "hardware" provided by the virtual machine.

The bottom line is that in both cases you are at the mercy of either Wine's performance or the hardware abstraction layer of the virtual machine software.  It may simply be that you will not get any better performance.

Add to that the fact that the hardware acceleration available in ATI's Linux drivers is not anywhere near as feature-rich as NVIDIA.

---

### Post by boat2 on 2013-10-14
You're missinterpreting. This has nothing to do with the performance of applications in wine nor vmware. After a reboot the natively running applications i.e dota2 run perfectly fine, I get a nice framerate between 50-80, until I've even once ran either something through wine or vmware where it suddenly caps dota2 at about 10fps. The issue is that something does something and suddenly what ran very well barely runs at all.

---

