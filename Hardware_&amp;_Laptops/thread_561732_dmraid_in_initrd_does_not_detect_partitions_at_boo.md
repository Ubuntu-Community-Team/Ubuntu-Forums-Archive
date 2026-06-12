---
title: "dmraid in initrd does not detect partitions at boot"
date: 2007-09-27
forum: Hardware &amp; Laptops
---

### Post by ktsaou on 2007-09-27
Hi,

I have a P4P800 mobo with its 2 RAID0 controllers active (Intel and Via).
I have managed to install ubuntu 7.04 by hand on the Via controller.

Everything works fine, except that at boot it stops with an initramfs prompt.
There, I have to write manually:

dmraid -ay via
exit

and it continues.
I have found that during boot, initrd runs:

dmraid -ay

but this alone does not load the partitions of the Via controller in /dev/mapper (although the partitions of the Intel controller are there!).
When I do:

dmraid -ay via

It loads the partitions of Via raid controller too, allowing the boot sequence to proceed.

Any ideas on how to automate this little think at boot?

Costa

---

