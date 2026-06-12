---
title: "sil3114 RAID-5"
date: 2005-08-27
forum: Hardware &amp; Laptops
---

### Post by yamla on 2005-08-27
My motherboard, a Gigabyte K8NXP-SLI, supports RAID5 with the SATA drives hooked up to the sil3114 sata controller.

Now, I'm fairly sure this is software RAID-5 and that's fine.  Right now, I have Ubuntu set up to use software RAID-5 for my /home partition, made up of a combination of SATA and PATA drives, and I'm willing to accept the speed/cpu issues.

What I'd like to do, though, is ditch my PATA hard drives and go to an entirely SATA RAID-5 system.  I dual-boot to Windows and I'd like to use RAID-5 there as well, the end result being that I want to do RAID-5 from the BIOS.

Does Hoary Hedgehog support that at all?  Would Breezy Badger?  What sort of issues will I run into?  I presumably would have to reformat my machine and I'm quite willing to do that.  Will Ubuntu see the four drives as ONE single drive, or will it ignore the BIOS RAID-5 setting and just see all four individual drives?

Please and thank you.

---

### Post by yamla on 2005-10-15
No, it turns out that Linux itself does not support this.  The dmraid tool works but the device mapper that is part of Linux does not support RAID5 targets.  The patches available at the usual place also don't seem to add this (though I could be wrong).  The end result is that at the moment, what I was trying to do is simply impossible in Linux.

This has nothing to do with Ubuntu, it's a limitation in the Linux kernel.  There's hope, though, as at least one person at NVidia is hoping to add this capability.

---

