---
title: "Problems with Lilo using Intrepid Ibex"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by vincencollins on 2009-03-01
I am having trouble with lilo after upgrading to Intrepid Ibex.  Whenever I updating anything lilo keeps failing.  I just get random garbage on the boot screen when I try to start up.  It is like the update is somehow overwriting lilo.  I have already reinstalled lilo once via the live disk but when I run lilo I get the following message.  

> Warning: The initial RAM disk is too big to fit between the kernel and
   the 15M-16M memory hole.  It will be loaded in the highest memory as
   though the configuration file specified "large-memory" and it will
   be assumed that the BIOS supports memory moves above 16M.

This only started showing up after I upgraded to Intrepid Ibex.  Before I only had to make sure to run lilo after kernel updates.

Also I have lilo installed to boot from a partition and not from from MBR.  I have been trying to avoid the MBR because I would like to have a duel boot one day.

I need to use lilo because grub wasn't allowing my cdrom to mount and the only solution that ever seem to work was switching to lilo.

Any ideas on what the root problem is and how I can fix this issue?

---

### Post by vincencollins on 2009-03-06
The only solution that I ever figured to this was to rename lilo.conf to lilo.conf.bak (basically remove) and then run liloconfig again.

That fixed the problem for now but I am still curious why this just started occurring with Intrepid Ibex.  If anyone please has insight into this please reply.

---

