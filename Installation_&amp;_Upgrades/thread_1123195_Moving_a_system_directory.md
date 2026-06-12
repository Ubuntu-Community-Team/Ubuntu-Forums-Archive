---
title: "Moving a system directory"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2009-04-11
Suppose I have installed Linux, then I decide to split...like the /var directory to a different partition...is it possible to do this without reinstallation or in that case without loosing settings or having to reinstall all the software?



I don't think so.

---

### Post by lykwydchykyn on 2009-04-11
It's quite doable, but it's best to do it offline while booted to a liveCD.  The basic gist of what you do is this:
 - boot to live CD
 - create new partition
 - mount old root partition
 - move data to the new partition
 - edit the /etc/fstab on the hard drive to point to the new partition
 - reboot

If you need help with the particulars, just ask!

---

### Post by iponeverything on 2009-04-11
It not big deal at all.  Just add new mount point to /etc/fstab

---

### Post by dE_logics on 2009-04-12
Ok...thanks people...I guess we got lots of article discussing on how to edit that.

---

