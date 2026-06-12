---
title: "How do i UNINSTALL Ubuntu ?????"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by mrexcluszive on 2009-10-19
how do i uninstall ubuntu and get rid of the GRUB loader to load my Windows partion?? i really really need this help asap ...

---

### Post by MelDJ on 2009-10-19
how did you install ubuntu?
if its on a different partition: go to windows, then go to computer management and format the ubuntu partition there.
if through wubi: uninstall ubuntu from add/remove

---

### Post by presence1960 on 2009-10-19
> **MelDJ said:**
> how did you install ubuntu?
**_if its on a different partition: go to windows, then go to computer management and format the ubuntu partition there._**
if through wubi: uninstall ubuntu from add/remove

That is only half the process if installed on a dedicated partition. Now you need to restore your windows bootloader to MBR or you will get a GRUB error when you boot because GRUB will be pointing to the partition you just deleted.

If you need help restoring windows to MBR post back.

---

### Post by B-Navigator on 2009-10-19
> **mrexcluszive said:**
> how do i uninstall ubuntu and get rid of the GRUB loader to load my Windows partion?? i really really need this help asap ...

Hmm, is your problem about trying to remove Ubuntu from your machine, or is it that during your instilation you found yourself unable to set up to log into windows?
  If it's the former, you probably want to use GParted to get rid of your Ubuntu partition and expand the windows partition, then use your windows disk to repair the windows boot system.
If the later, then you actually should be able to edit GRUB to boot into windows, though I'd have to search for the method myself.

---

### Post by gchand7 on 2009-10-19
use widoows to remove youe ubuntu partition and then                                                                                                   Boot from xp cd
r to repair
select windowa partition
fixboot
yes
fixmbr
yes
restart

---

### Post by saif_held on 2009-10-19
Or if you want to have Vista, just put the DVD let it boot, and go to repair my computer. From command prompt type:

Bootrec.exe/ FixMbr

restart & done

---

