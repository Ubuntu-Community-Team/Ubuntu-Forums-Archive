---
title: "RAID 5 fresh install (Grub Error 2)"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by champi0n on 2009-07-16
I've done a fresh install with the alternate CD, and AFIK successfully installed software RAID5 for 3 disks having 3 partitions each. (boot, root, and swap)

Which translates into:
MD0 (200MB) ext3 /boot -- *partitioned each disk with 100mb boot flag (primary)*
MD1 (8GB) swap -- *partitioned each disk with 4gig swap (logical)*
MD2 (~2TB) ext3 root / -- *partitioned each disk with ~1TB / (primary)*

Now the problem is after the installation, the system reboots and after stage 1.5 of GRUB it comes up with GRUB ERROR 2.

I'm assuming that the GRUB is pointing to hd0 (0,0) instead of md0 (0,0) or something? Is this not the case? Anyone have a fix to this or experienced this problem before?

I'd of course want grub/boot to be the same on all drives in case one fails, but shouldn't this have been taken care of when I setup the software raid during the install?

thanks for any help.

---

### Post by dstew on 2009-07-16
At present, grub stage1.5 cannot read from a striped RAID, like RAID 5. It you want to have your Ubuntu system on a striped RAID, that is fine, but grub needs either a mirrored RAID, like RAID 1, or a non-RAIDed partition to get its stage2 from.

What I have done is to make the /boot partition on a small RAID 1, and have the rest of the system on a RAID 5. That works OK. Actually, grub cannot really handle a RAID 1 either, but it reads from the targeted partition, not knowing that it has a twin elsewhere.

---

### Post by champi0n on 2009-07-16
Cool, got it all setup and working.

Just changed the 100MB /boot partition to RAID1 (mirrored across the 3 drives) instead of RAID5.

All works and I think that was the better solution to keep the system bootable if a drive fails.

I'm getting 41% CPU on "md2_raid5" though... seems a bit high (about 10% on each core). And load average of 2.00 1.94 1.55

Hard to say if this is because its the initial run in of the array or if it'll stay this high.

---

