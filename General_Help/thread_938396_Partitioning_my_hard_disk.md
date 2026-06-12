---
title: "Partitioning my hard disk"
date: 2008-10-04
forum: General Help
---

### Post by SonicRacer1412 on 2008-10-04
/dev/sda1   (Caution icon)   ntfs        150.90 GiB     ---     ---  boot
/dev/sda2                    ext3   /    145.05 GiB     6.68 GiB 138.37 GiB
/dev/sda3   (Lock Icon)      extended    2.14 GiB       ---     ---
   /dev/sda5  (Lock Icon)    Linux-swap  2.14 GiB       ---     ---

Does this look familiar to you. I am planning on a rescue plan for our family's computer to get our hard disk erased and start all over again and by dual-booting the RIGHT way (the wrong way resulted in the Windows boot screen before the infamous _UNMOUNTABLE_BOOT_VOLUME error). This (the above listings) is what is seen when I use GParted from the Ubuntu 7.10 Live CD. How do I unlock sda3 and sda5?

---

### Post by louieb on 2008-10-04
Looks like the live cd is using the linux swap partition. In GParted Right click on the partition /dev/sda5 and select swapoff. That should remove the locks.

---

