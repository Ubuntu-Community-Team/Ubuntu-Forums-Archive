---
title: "installation of ubuntu server problems"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by Milambar on 2009-02-11
Im trying to install a small server on an old PC to use for testing webdesigns.

I downloaded the ubuntu server cd, and let it run through the setup, but it doesn't seem to create the partitions on the hard disk correctly.

I expected:

/     - the root partition
/home - the home partition
/opt  - the partition for optional packages
and a swap partition.

At the very least I want /, /home, and swap, I can live without /opt if I have to.

What I got was, / and swap, with /home just being a normal directory under /, and no option to configure it otherwise unless I hack through the rather unfriendly manual partitioner.

Whats going on guys? That partition setup (/ and swap) is more for a desktop setup, NOT a server.

Or have I overlooked something?

---

### Post by Pumalite on 2009-02-11
Use Gparted Live CD an prepare the partitions at your hearts content ahead of time:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
Then install, go 'Manual' and use the already prepared partitions.

---

