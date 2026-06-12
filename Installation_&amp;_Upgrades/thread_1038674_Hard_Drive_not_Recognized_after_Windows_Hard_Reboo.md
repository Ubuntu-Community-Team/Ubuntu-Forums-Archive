---
title: "Hard Drive not Recognized after Windows Hard Reboot"
date: 2009-01-13
forum: Installation &amp; Upgrades
---

### Post by gleslie07 on 2009-01-13
Unfortunately, I'm stuck with Windows Vista on my main computer.  I've run Ubuntu on my other computer and laptop for a little over a year now, so I'm somewhat familiar with it at this point.

I had a string of problems with Vista for a while.  iTunes would often crash (just starting recently), and Vista would become unresponsive.  I had to do a hard-reboot on one occasion, and I was greeted with something along the lines of

```

Windows cannot start because a required boot device is missing

```

I'm having trouble recreating it because:

C:\ Holds Windows
and
D:\ Holds the Recovery Partiton

and it's automatically booting the Recovery Partiton.

At this point, I would normally boot the recovery partition or use a recovery disk but I am given a BSOD (on a recovery disk?) about one of the ".sys" files Windows loads when starting the recovery console.

I proceeded to use my trusty Ubuntu 7.10 Live CD and upon booting Partition Editor (gparted), the drives are not located.  Any of them.  There are the two partitons on /hda and a flash drive on /sda (I think).

BIOS, for the record, recognizes the HDD.

And to make things even better, *as I was writing this* my hard drive started making that ominous clicking sound I so dread, and Ubuntu greets me with a infinite loop of:

```
Buffer I/O error on device sda1, logical block 0
```

Any ideas to at least recover the data?

Thanks.

**EDIT:** set my desktop out for repairs for the failing HDD.  I got most of my stuff backed up so I guess it will be ok.

---

### Post by mikewhatever on 2009-01-14
Hi there,
please post any further Windows related threads in the Windows section.
You can try recovering your data with SystemRescue live cd.

---

### Post by gleslie07 on 2009-01-14
> **mikewhatever said:**
> Hi there,
please post any further Windows related threads in the Windows section.
You can try recovering your data with SystemRescue live cd.

Sorry, new here (obviously).

I thought I read somewhere that Knoppix can read damaged disks.  Does anyone know if a bootable DSL live cd would be able to read it?

---

