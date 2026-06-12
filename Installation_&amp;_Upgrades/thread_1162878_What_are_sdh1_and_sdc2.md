---
title: "What are sdh1 and sdc2"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by doublej on 2009-05-18
After upgrading my ATI video driver under Jaunty my Ubuntu will not load. I keep getting the following error messages:

Failed to access volume /dev/sdh1 - no such file or directory, NTFS signature is missing

Failed to mount /dev/sdc2 - invalid argument, does not seem to have valid NTFS

The computer is dual booted with WinXP and all the drives are accessible in Windows. I get the same message in recovery mode as well.

So what are /dev/sdh1 and /dev/sdc? And how do I fix things. 

Cheers

John

---

### Post by jerrrys on 2009-05-18
if you start your count at one and not zero; its saying that hard drive #3 (sdc), partition #2 and hard drive #8 (sdh), partition #1 is not a readable NTFS format...

---

### Post by Mark Phelps on 2009-05-18
> **doublej said:**
> So what are /dev/sdh1 and /dev/sdc? And how do I fix things. John

From a terminal, enter "sudo fdisk -lu" (that's a lowercase L, not a one).  That will provide a listing of "drives", actually, partitions in Linux terms, which will show you which partition matches which device.

My guess is that you're mounting Windows partitions at boot time, most probably using your /etc/fstab file. One way to fix this would be to boot using an Ubuntu Live CD and edit the fstab to comment out the Windows partition mount lines, and save the edited file.  Once you do that, you should then be able to reboot normally.

---

