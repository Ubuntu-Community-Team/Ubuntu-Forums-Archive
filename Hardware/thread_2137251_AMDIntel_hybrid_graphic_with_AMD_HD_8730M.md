---
title: "AMD/Intel hybrid graphic with AMD HD 8730M"
date: 2013-04-20
forum: Hardware
---

### Post by ppierpaolo on 2013-04-20
Hi everyone :)

I've got an** AMD HD 8730M** / **Intel HD Graphics 4000 **hybrid Graphic card and I recently installed Ubuntu 12.10.
Ubuntu only recognizes my Intel HD Graphics card, and this causes my Dell Inspiron 15r 5521 to overheat.
I installed and configured the package for fan control (i8kmon) but this is not a solution for my problem, since I want to be able to use all my graphic hardware, and not only the intel graphic card.

What can I do? How can I entirely use my hybrid graphic card? I don't want to delete Ubuntu and go back to Windows.
Thank you in advance, I hope you have a solution for my problem.

P.S. I already took a look at this thread ([http://ubuntuforums.org/showthread.php?t=1930450&highlight=amd+graphic+card](http://ubuntuforums.org/showthread.php?t=1930450&highlight=amd+graphic+card)) but I haven't found a solution for my problem.

---

### Post by JMED106 on 2013-06-07
Hi there!

I have the same problem, the drivers provided by AMD don't work.
(Note, I use Debian Wheezy).

If anyone has a solution...

---

### Post by Mark Phelps on 2013-06-07
> **JMED106 said:**
> Hi there!

I have the same problem, the drivers provided by AMD don't work.
(Note, I use Debian Wheezy).

If anyone has a solution...

That's  because the Linux drivers from AMD do not support AMD/Intel Hybrid graphics; instead, they are intended for PCs where the AMD video chipset is the only one in use.

As you can see by reading the linked thread, there is no simple solution to the Hybrid Graphics problem -- in Linux.

---

