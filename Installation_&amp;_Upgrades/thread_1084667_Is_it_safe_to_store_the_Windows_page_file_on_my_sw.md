---
title: "Is it safe to store the Windows page file on my swap partition?"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by digitalbenji on 2009-03-02
Hi,
   I dual-boot XP and Linux on some systems, and to save disk space, I'm wondering if its dangerous to store my XP pagefile on my ext2 swap partition.  I use the fs-driver.org driver so that I can mount ext2 partition in Windows, and I already share my home directories this way.  I guess the only gotcha I see is if windows expects the pagefile to have some kind of information that persists from 1 boot to the next, and if Linux will just use the swap partition as it should regardless of having some file stuffed into it.

Anyone know?

Thanks,

---

