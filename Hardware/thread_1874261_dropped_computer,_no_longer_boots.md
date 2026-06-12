---
title: "dropped computer, no longer boots"
date: 2011-11-02
forum: Hardware
---

### Post by patman0623 on 2011-11-02
I dropped my desktop computer today while transporting it, and it doesn't boot properly anymore. It also had trouble hibernating right before I dropped it, so I'm not sure which is cause behind the problem. I can't be sure but I suspect the disk is corrupted. 

Anyway, the normal grub 2 screen comes up. I am able to boot into Win7 on my alternate disk, where I can still see the Linux ext4 file system. But when trying to boot into Ubuntu, I get a kernel panic and it jumps into BusyBox.

How can I fix my Ubuntu installation?

---

### Post by jwbrase on 2011-11-02
> **patman0623 said:**
> I dropped my desktop computer today while transporting it, and it doesn't boot properly anymore. It also had trouble hibernating right before I dropped it, so I'm not sure which is cause behind the problem. I can't be sure but I suspect the disk is corrupted. 

Anyway, the normal grub 2 screen comes up. I am able to boot into Win7 on my alternate disk, where I can still see the Linux ext4 file system. But when trying to boot into Ubuntu, I get a kernel panic and it jumps into BusyBox.

How can I fix my Ubuntu installation?

What exact message do you get with the kernel panic?

How to go about fixing your installation depends on the type of damage you're dealing with. Just a warning ahead of time: if the disk Ubuntu is on was damaged when you dropped it, your installation is most likely hosed.

---

### Post by trundlenut on 2011-11-02
First off I would make sure that everything is still connected properly inside, I would unplug and replug everything (discs, memory power supply etc).

Stage 2 will probably look to do diagnostics on the disc.  Try something the UltimateBootCD and use the hard drive and memory diagnostic tools.

---

### Post by patman0623 on 2011-11-03
Used an Ubuntu startup disk and ran e2fsck -c -c -f which fixed it (although I had to run it under a few different options, a few different times). Fortunately, only files in /var/log/ were corrupted.

---

