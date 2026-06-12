---
title: "What happened to my partition?"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by evilwombat on 2009-03-02
I was installing Ubuntu 8.10 on my computer with the hope of dual booting with vista. I ended up closing out of the partitioner after a solid 20 minutes on 0%. Now Windows freezes on a black screen before it can boot up. What should I do? Will a system restore disc fix this?

---

### Post by blackened on 2009-03-02
Without more info on the drive layout and filesystem types I can't give you any insight as to why the partitioning failed.

If you can get to the Vista recovery console using aforementioned "system restore disc" then you should be able to use "fixmbr" to resolve the Vista boot problem.

---

### Post by Mark Phelps on 2009-03-02
You should NOT use the Ubuntu partitioner to resize your Vista OS.  While it generally works, in those situations where it doesn't, it leaves Vista in a state where it won't boot to the OS anymore -- until you boot from a Vista DVD or Vista Recovery CD and run Startup Repair.

You do have such a disk, right?

If not, checkout the NeoSmart forums where you can download and burn a Vista Recovery CD.  Burn and boot from that CD, and run a Startup Repair.

After that, use Disk Manager in Vista to shrink the Vista OS partition.  IF you have problems doing the shrinkage, come back.

---

