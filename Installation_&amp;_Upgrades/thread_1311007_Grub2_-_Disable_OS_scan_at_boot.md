---
title: "Grub2 - Disable OS scan at boot"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by mithrandir77 on 2009-11-02
Hi all,

I am new in this forum.
I have just installed ubuntu 9.10 (64bit) version and I like all its new features.
But I don't like a new feature of grub2: each time I start my system, it checks all the drives to find all the OSs available. I found on grub2's guides that it can be disabled adding GRUB_DISABLE_OS_PROBER=true option in /etg/default/grub file. But it seems to disable system scan both during update-grub and during system boot: so after run update-grub it seems to generate a grub.cfg containing only the running system and no other OSs I have installed and I suppose that after rebooting I can load only ubuntu 9.10.
Is there a way to generate the grub.cfg with update-grub containing all the available OSs (just manually), and then to disable drives scan at boot time? I have two disks, ubuntu 9.10 and 9.04 installed (this one with 3 kernels) and windows XP, and grub2 takes at least 8/10 seconds to scan the system and show its menu.

---

