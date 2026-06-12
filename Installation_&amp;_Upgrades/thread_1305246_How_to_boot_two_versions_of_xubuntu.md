---
title: "How to boot two versions of xubuntu"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by mesmith on 2009-10-29
Is there a tutorial on how to install two different versions of the same os (xubuntu in my case) for dual boot?

---

### Post by tonyyarusso on 2009-10-30
I'm not sure if there's a specific tutorial, but basically all you need to know about is partitioning, and the rest is just installing twice.  Depending on what you're doing you may want to share your /home between the installations, in which case you can just make it separate in the first install and select it at the partitioning stage of the second installer.

---

### Post by mesmith on 2009-10-30
If xubuntu 8.10 is installed and I add 9.10 in another partition, what version of grub will I end up with?

---

### Post by paulyg on 2009-10-31
> **mesmith said:**
> If xubuntu 8.10 is installed and I add 9.10 in another partition, what version of grub will I end up with?

If you let the installer do the default it will overwrite the MBR with grub2 but you can tell the installer not to overwrite the mbr. In that case you will have to edit your menu.lst file in your 8.10 install and add a line to point to the 9.10 install.

---

