---
title: "Duel boot with dedicated kernel subdirectories"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by Bunnykun on 2009-01-09
Hello!
Currently, I am duel booting Ubuntu and Ubuntu Studio.  I want to keep the kernel files separated, so I have the kernels in subdirectories under /boot, which is mounted on a 100mb ext2 partition.  My (manually edited) grub menu finds the kernels with no problem.

The problem (really, just an annoyance) is that when the kernel is updated, the new kernel files are placed in /boot and not in /boot/<respective distro kernel subdir>.  When the update requires referencing the original files, it also looks in /boot.  When this happens, I have to copy the files back and forth etc etc.  Like I said, really just an annoyance, but the limited partition size sometimes becomes an issue too.

Now the question: is there a way to get the updates to look in different places for the kernel info?  Or maybe use sym link trickery so that /boot uses the default hierarchy for the distro that I'm currently using (ignoring the other kernel folders)?  would grub be able to follow sym links in the first place?  

Any ideas?  I'm ok with babysitting the kernel updates, but streamlining is always awesome.

---

### Post by lemming465 on 2009-01-10
I don't see why the symlink approach wouldn't work. Yes, grub can follow symlinks.

---

