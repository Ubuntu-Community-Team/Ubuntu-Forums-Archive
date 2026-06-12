---
title: "last good boot disappeared after grub install"
date: 2008-10-15
forum: General Help
---

### Post by jithin1987 on 2008-10-15
After resizing my root partition by deleting some other partitions, I had to reinstall my grub.
After that I edited menu.lst to reflect the changes of my root partition and swap partition (swaps UUID changed).
But i no longer has the last good boot entry. I also noticed that now there is no /boot/last-good-boot directory which has this files.

I use kubuntu 8.10 beta. Any help aprreciated:)

---

### Post by shawnrgr on 2008-10-15
Did you run 'sudo update-grub' ?

---

### Post by jithin1987 on 2008-10-20
Is seems that last good boot has been rolled back by ubuntu.
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/284210](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/284210)

---

