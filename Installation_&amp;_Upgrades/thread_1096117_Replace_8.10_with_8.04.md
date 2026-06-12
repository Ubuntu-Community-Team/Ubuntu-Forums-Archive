---
title: "Replace 8.10 with 8.04"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by MilesF on 2009-03-14
I installed ubuntu 8.10 on my windows XP computer that partitioned my hard drive into 50% windows XP and 50% ubuntu 8.10. I later realized that I wanted to install ubuntu 8.04 instead.

When I try to install ubuntu 8.04, I cannot figure out how to tell it to install over ubuntu 8.10 in the partitioning menu. The two options that I understand are "Guided - resize" and "Guided - use entire disk." The problem is that neither of these options seem like they will work. "Guided - resize" only looks at the first partition of my hard drive where windows XP is installed, so if I select this option I will end up with something like 25% windows XP, 25% ubuntu 8.04, and 50% ubuntu 8.10. The other option, "Guided - use entire disk," appears to look at both partitions and will leave me with 100% ubuntu 8.04. 

The "Manual" mode gives me the most options, but I don&#8217;t know how to set it up correctly with the mount point, swap partition, etc.

Is manual mode the way I should be doing this, and if so, what are the steps? Or do I need to do something else like going back to 100% windows xp first and then install 8.04?

Thanks

---

### Post by 67GTA on 2009-03-14
Choose manual, select the current Ubuntu partition, choose ext3 as the file system, and "/" as the mount point.

EDIT: To do this, select the Ubuntu partiton and then select "Edit".

---

### Post by MilesF on 2009-03-14
That worked great. Thank you

---

