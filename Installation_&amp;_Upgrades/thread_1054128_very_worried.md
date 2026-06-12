---
title: "very worried"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by polskimoose on 2009-01-29
i got my desktop computer to dual boot with Windows XP and Ubuntu, however, the boot disc i installed ubuntu with was not at all perfect, so my ubuntu is screwed up.  basically, i want to try again using wubi, however, i would like to uninstall the ubuntu that i have on there first, removing the dual boot before i try again.

basically, i have no idea where to start.:confused:

---

### Post by polskimoose on 2009-01-29
anyone?

---

### Post by SqRt7744 on 2009-01-29
easier said than done. You will have to remove the partition created for ubuntu. You will need a partition manager (you could boot off the live ubuntu CD, start gparted (system->admin->partition editor) and delete the ubuntu partition. Unfortunately I can't say whether the boot loader (GRUB) will still be able to start windows without you repairing the windows install with the XP cd or reinstalling grub... but... what exactly is 'screwed up' about you ubuntu install? It might be eaiser to reinstall it instead of deleting the partition.

---

