---
title: "Motherboard upgrade - boot cannot find drives - G43 problem?"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by eyekode on 2009-09-24
First some background:

My old motherboard died (Intel platform G31 chipset?) and I temporarily swapped it for an AMD platform board.

This machine runs 8.04.

My new motherboard came in (G43 chipset) and I swapped it into the system.

Now the boot process cannot find the drives. I get the Ubuntu splash screen and then a message about not being able to find the root's UUID and I get dropped into a shell.

I tried to boot from the 8.04 CD and it comes up but it cannot see any of the drives. blkid does not list any of them. I even tried to "install" from the CD but the partitioning stage cannot see the drives either.

So I tried a 9.04 CD and it can see the drives.

I guess this is a problem with the new chipset not being supported by the old kernels?

What is the best way to fix this? I do not want to blow away my old partion/setup so installing directly from the 9.04 looks out of the question.

One idea I have is to put the drive back in the AMD system and do the upgrade to 9.04. Then swap the drive back into the G43 chipset board.

Any other ideas?
Thanks!
Salem

---

### Post by rreese6 on 2009-09-24
You do have a good one. 
It would appear that you do not have the right module loading into the kernel. and the new kernel contains what you need.
you last idea would be the easiest attempt to correct the problem.
otherwise you would need to taint your current kernel with a driver module and that might be a disaster. Another way might be to back up your home directory and do a fresh install, then restore your home directory.

let us know how it works out.

---

### Post by eyekode on 2009-09-25
The process seems to have worked with one unrelated problem. When I upgraded from 8.04 to 8.10 to 9.04 at the end my raid array stopped getting assembled correctly.

But at least the new motherboard is working :). On to the next problem.

---

### Post by eyekode on 2009-09-25
> **eyekode said:**
> The process seems to have worked with one unrelated problem. When I upgraded from 8.04 to 8.10 to 9.04 at the end my raid array stopped getting assembled correctly.

But at least the new motherboard is working :). On to the next problem.

Good news :). I had an issue with the UUID of the raid array, for some reason it changed when swapping MB's and versions of Ubuntu. I let mdadm discover the correct mdadm.conf line and all is happy :).

---

