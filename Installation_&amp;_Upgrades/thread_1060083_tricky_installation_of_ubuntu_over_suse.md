---
title: "tricky installation of ubuntu over suse"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by ray field on 2009-02-04
after getting my feet wet with Intrepid on a little eee PC, I want to install it on my secondary desktop box, an Asus Pundit with a dual-core AMD, which has SUSE 10.2 coexisting with XP thanks to Grub.  I'd like to wipe out SUSE but preserve how the startup Grub menu is working, because down the road I'd also like to be able to continue to use OS/2's boot manager (which the SUSE grub correctly lists as a bootup option) -- I can't remember exactly where Grub is placed but I do know it's got to stay where it is in order for it to recognize both OS/2's Boot Manager and XP.



how can I 1) tell how Grub is installed and 2) be sure that whatever Ubuntu does, it will preserve the entries as they're presently configured, and 3) if anyone knows, simply wipe out Suse before installing Ubuntu with essentialy the same disk layout?

---

### Post by Pumalite on 2009-02-04
Install; go 'Manual' and choose the old suse partitions. You can ignore /swap. You'll have a brand new Grub and dual boot.

---

### Post by ray field on 2009-02-04
> **Pumalite said:**
> Install; go 'Manual' and choose the old suse partitions. You can ignore /swap. You'll have a brand new Grub and dual boot.

I certainly hope so, thanks!

---

### Post by ray field on 2009-02-05
> **Pumalite said:**
> Install; go 'Manual' and choose the old suse partitions. You can ignore /swap. You'll have a brand new Grub and dual boot.

um in fact it's stalled, with:

```
GRUBLoading Stage 1.5

GRUB loading, please wait...
Error 2
```

just to recap what I did: I chose Manual, and carefully selected the Suse partitions (not that hard as they were already formatted ext3).

then, before committing to the installation, I specified that Grub go into the / partition, where I'm pretty sure it needs to be for the sake of OS/2's boot manager and to make things simpler with XP.

how to fix?

---

