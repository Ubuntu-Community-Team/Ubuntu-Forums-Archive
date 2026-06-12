---
title: "REINSTALL PARTITIONING PROBLEM s:"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by cusinmex on 2009-10-21
hi there folks..noob here C:

ive been using ubuntu now for approximately 5 months
and ive been satisfied and im happy with ubuntu
but i haven't used windows since then. when
i try to boot into windows..windows is so slow that
 takes about 15 min for it to load anything at startup
im not really sure what caused that suddenly S:

so i was considering **reinstalling windows..** but
word on the street is  that reinstalling the windows partition
will cause me to lose ubuntu as well D: .

i dual boot XP and Ubuntu 9.04 with GRUB

so my question is can i *reinstall the windows partition *when
i already have an ubuntu partition?

if not is there a way around this?

any help is appreciated thanks in advance

---

### Post by Mark Phelps on 2009-10-22
If you have XP on its own separate partition, reinstalling will not wipe out Ubuntu, but it will wipe out the GRUB entries in the MBR.  You will then have to boot from an Ubuntu LiveCD and restore GRUB.

---

### Post by cusinmex on 2009-10-22
but none of the data on ubuntu will be lost?

---

### Post by mechro on 2009-10-22
> **cusinmex said:**
> but none of the data on ubuntu will be lost?

As long as you don't resize, delete or move any partitions then it won't affect Ubuntu unless you make a mistake. So when you tell Windows where to install you should make doubly sure it's the right partition.

As mentioned, you'll have to restore Grub.

---

### Post by oldfred on 2009-10-22
It is always safer to have backups of any important information.

More info on reinstalling grub:
restore boot loaders Ubuntu Win xp Vista
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

15 minutes is too long for any operating system. Have you tried chkdsk, defrag or other diagnostics on your system? But, it may be quicker & easier to just reinstall.

---

### Post by cusinmex on 2009-10-23
so what would be the best?

reinstall windows with out
uninstalling it first?

so im supposing that the actual oS 
is different than partition.. 2 diff things?

sorry for question
im new to this linux stuff

---

