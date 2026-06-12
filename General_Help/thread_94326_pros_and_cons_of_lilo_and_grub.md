---
title: "pros and cons of lilo and grub"
date: 2005-11-23
forum: General Help
---

### Post by Specialsauce on 2005-11-23
what are the differences? there has to be some? Which do you recommend, Lilo, or Grub?

---

### Post by matthew on 2005-11-23
Lilo is older and still in widespread use. Grub is newer and seems to be more flexible, or at least more easily configured and modified.

Ubuntu uses grub by default so you are most likely to find people familiar with it here.

Here are some sites to take a look at.

[http://www-128.ibm.com/developerworks/library/l-bootload.html?ca=dgr-lnxw01LILOandGRUB](http://www-128.ibm.com/developerworks/library/l-bootload.html?ca=dgr-lnxw01LILOandGRUB)
[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)
[http://www.acm.uiuc.edu/workshops/linux_install/lilo.html](http://www.acm.uiuc.edu/workshops/linux_install/lilo.html)

---

### Post by SilentCacophony on 2005-11-23
That pretty well sums it up, in my experience. I've seen a couple of special applications where lilo seemed to be preferable to grub, but grub seems to have usurped lilo's position in most of the recent distros that I've tried. It is a bit less cryptic to the beginner, as well, IMO.

There are also other bootloaders that can be made to work, sometimes in conjunction with grub or lilo. For example, I used to use Ranish Partition Manager to multi-boot several Windows/DOS installations. While it can be used to chainload linux partitions with grub installed to the *partition* (rather than the MBR of the disk, where Ranish would be,) I found that I like grub well enough as it is.

---

