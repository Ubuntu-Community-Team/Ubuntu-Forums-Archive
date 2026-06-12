---
title: "GRUB: Error 18 - is it possible to occur after HDD hardware failure?"
date: 2008-10-13
forum: Hardware
---

### Post by laleelay on 2008-10-13
Hi!

I have set up a dual-boot system: Windows XP SP2 and Ubuntu 8.04, standard install, GRUB being the boot manager.

Unfortunately the system is in another town (my parent's place) and since today it gives Error 18, displays the boot menu but refuses to load any OS. I have read couple of posts about this error and know that it most often means that the MBR is messed up (might be wrong there).

I have strong reasons to believe that the cause is hardware malfunction of the old 80GB Maxtor ATA HDD.

My question is does anyone knows if this Error 18 is only due to software problems/bad sectors in the MBR, or you can get that one after a hard drive goes "dead"... But then why it should display the boot menu?

Thanks 2 all!

---

### Post by laleelay on 2008-10-13
Here is the description of Error 18: 

"Selected cylinder exceeds maximum supported by BIOS. This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area."

Usually it occurs when a larger disk is set up in an older system. This is not the case, I have been using different OS-s on that HDD (with Grub as boot manager).

I am afraid that the only logical explanation is that the readable part of the hard drive has been suddenly shrinked to a small space due to permanent hard drive damage.

I only hope that the files are recoverable.

Any suggestions?

---

