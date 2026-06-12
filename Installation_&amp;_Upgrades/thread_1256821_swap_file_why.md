---
title: "swap file why?"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by ottosykora on 2009-09-03
I updated 8.10 to 9.04 ubuntu.

I noticed that during the booting 'swap file' was created.
This came up only in the 9.04.
After few starts, the swap file creation went for ever, the boot process got stuck. I tried to interrupt it by obvious like ctrl+c, but only after I pressed crtl+alt+del the booting continued.
I noticed that the partition filled after each boot more end more, resulting now that a standard installation is about 8gb in size and I can not boot any more since no space on the disk for opening profile and so on.

Can this swap file be somehow avoided or stopped? Why can the 9.04 not use the usual swap partition?

A wubi installation of 9.04 is already impossible due to this swap file, so why not avoid it at all?

---

### Post by bryanl on 2009-09-03
It sounds like a new swapfile is being created on each boot. Why your setup does this I don't know. If I boot Ubuntu here without a swap partition or file, it just complains and then goes on with its business.

See [Move to swapfile rather than swap partition](http://tcl.leipper.org/?p=992) for how a swap file is established and how you need to identify it in fstab. Maybe that will provide some ideas.

---

### Post by ottosykora on 2009-09-07
> **bryanl said:**
> It sounds like a new swapfile is being created on each boot. Why your setup does this I don't know. If I boot Ubuntu here without a swap partition or file, it just complains and then goes on with its business.

for how a swap file is established and how you need to identify it in fstab. Maybe that will provide some ideas.

well meanwhile I was able to little  bit , but not in detail, find what is the problem.

it only concerns wubi installation 9.04, not eralier installation. That means there was a wubi installation 8.10 and was upgraded to 9.04.
All setting in it want swap file. Fine, but the 9.04 seems to see a swap partition on same harddrive and thought the common entries as in the fstab point to the swapfile, it gets mixed up by the presence of the swap partition. It tries to 'activate the swapfile' but produces some kind of nonsense swap.
If swap partition is present and one manages to delete the swapfile properly, the booting is no problem and one can set the swap partition as swap later in fstab.
If swapfile is present and the all points to it as swap space and swap partition is present as well, all gets mixed up and booting is will do some unpredictable actions as it seems to me.

---

