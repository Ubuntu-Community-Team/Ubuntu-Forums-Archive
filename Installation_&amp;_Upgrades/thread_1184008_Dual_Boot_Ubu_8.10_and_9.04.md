---
title: "Dual Boot Ubu 8.10 and 9.04"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by dernsber on 2009-06-10
Ok, weird request, i know, but i have what i think is a decent reason.

When i installed 9.04 it broke a LOT of stuff on my laptop... so i would like a testing environment exactly like the laptop but not hurting my primary OS.... 

Long story short, does anyone know of a good guide in setting up a dual boot with other Linux OSes, so i can play with them that way instead of in VMs?

Thanks!!

---

### Post by presence1960 on 2009-06-10
Just create a partition for the "test" distro and install to that partition using the "manual" install option at the prepare disk space Window of the partitioner.

Myself personally I would install GRUB of the test distro to that partition and chainload that off your "main" OS menu.lst. This way when each distro updates their kernels you won't need to edit each menu.lst to include the new kernels.

---

### Post by dernsber on 2009-06-11
ok... somewhat makes sense... 

Sense i have my HD currently fully partitioned... what would be able to shrink that partition down?... guessing a boot to CD and do it that way...

---

### Post by dernsber on 2009-06-11
Ok, using the GParted from the boot CD of 9.04... hopefully i can figure out the other stuff you said... 

Anyone else have a good ref site for setting up dual boot systems in general?

---

