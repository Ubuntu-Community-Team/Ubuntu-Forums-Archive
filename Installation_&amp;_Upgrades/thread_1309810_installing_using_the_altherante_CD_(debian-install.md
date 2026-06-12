---
title: "installing using the altherante CD (debian-installer)"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by pimavegan on 2009-11-01
Just an FYI to people using the alternate CD to install ubuntu 9.10 in multi-boot systems. The installation will put grub2 in the incorrect boot partition (one number lower). Grub2 started naming partitions from 1, while the previous version started from 0. Apparently, the installation instructions during the install wasn't updated. 

To fix it, I booted to the OS that the ubuntu install wrote over. This booted to ubuntu. Then at a root shell ran the following to install grub2 in the correct partition:

grub-install /dev/sdaN 

where sdaN is the partition ubuntu was installed. It gives some nasty warning about installing grub2 into a partition, but it did work. 

I tried to open a bug report on launchpad, but it seemed too convoluted a process and I could never get to where I needed to go so I'm posting this in a forum instead.

---

### Post by stevepaul on 2009-11-01
Is this the same as the Ubuntu Alternate CD Installer ?

---

