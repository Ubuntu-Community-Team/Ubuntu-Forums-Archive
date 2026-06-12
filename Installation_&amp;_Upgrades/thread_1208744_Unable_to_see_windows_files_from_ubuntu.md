---
title: "Unable to see windows files from ubuntu"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by mxgeldar on 2009-07-09
Hi

Working on a second machine now and it is not behaving in the same way as the first one I installed.

All appears to have worked perfectly but I cannot see the old Windows files (and all my data) on the disks on this machine.  They are simply not there.  All that I can see are the linux filesystems.  Other than this it is perfect!

Any idea what I may be missing?

Thanks

Mark

---

### Post by Ashish Meena on 2009-07-09
Two possibilities which come to my mind
1. was your windows partition shut down properly or did you use hibenate for windows?
In both the cases partition is marked as being used which might be causing problems.
2. your partitions might not be mounted properly. Check /etc/fstab file.
For more info on /etc/fstab google is always here :)

---

