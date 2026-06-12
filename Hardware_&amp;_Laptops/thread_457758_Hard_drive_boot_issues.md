---
title: "Hard drive boot issues"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by drosenbauer on 2007-05-29
I'm having some issues with my local drives during boot. I recently upgraded (using apt-get) from dapper to edgy. With edgy came the new UUID style of drive identification. However, when I rebooted the machine after updating, I found myself at the emergency shell with a drive check error.

Fsck had exited with the following message:

[INDENT]fsck died with exit status 8[/INDENT]

After I watched really closely for several reboots, it appears that one of the UUIDs cannot be found. The system boots normally if I exit the emergency prompt. I reverted back to the old-style fstab (with /dev/hda2, etc), and it worked fine.

I also notice that I'm receiving something similar to the following message on startup:

[INDENT]Loading hardware drivers... Fail![/INDENT]

---

