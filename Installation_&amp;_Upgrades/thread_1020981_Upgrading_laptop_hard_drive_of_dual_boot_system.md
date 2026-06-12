---
title: "Upgrading laptop hard drive of dual boot system"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by jkwon19 on 2008-12-24
I have a laptop with an 80GB hard drive, with Windows XP and Ubuntu 8.04 running in a dual-boot configuration (I select the booting OS with grub).  I wanted to upgrade to a larger hard drive, and resize both the Windows and linux partitions, and was wondering what is the recommended method for doing so.

The disk appears to first have a fat16 boot partition, then the ntfs windows partition, then an extended partition containing the ext3 linux root fs and the linux swap partition.

My first thought was to dd the entire 80GB drive to a larger 250GB drive, then attempt to move and resize partitions in place using gparted.  However, with gparted, I am unable to move the start of the linux extended partition closer to the end of the new hard drive in order to expand the ntfs partition.

Can I create a new extended partition towards the end of the disk in the unpartitioned space, then cpio the contents of the linux extended partition to that new partition, and then destroy the original linux extended partition and grow the ntfs partition?

I'm guessing moving the start of the linux partition may affect the grub boot as well; can I easily modify the grub configuration to point to the new ext3/swap partitions?

Thanks,

Jason

---

### Post by upchucky on 2008-12-24
yes.

if you have trouble, knoppix has all the tools on it's live cd to manage partitions, edit menu.lst and grub.

Advanced supergrug can set up the new mbr cause it will get messed up by the partition work.

---

### Post by logos34 on 2008-12-24
> **jkwon19 said:**
> However, with gparted, I am unable to move the start of the linux extended partition closer to the end of the new hard drive in order to expand the ntfs partition.


Is the /swap mounted by chance?  Sometimes when you boot into the live cd desktop it activates the swap partition which, if on a logical partition, locks the extended so you can't resize.

Also, you need to shrink / first before you can resize the extended.

try that first

---

