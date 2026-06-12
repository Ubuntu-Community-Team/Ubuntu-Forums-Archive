---
title: "installing ubuntu server to nvidia raid5"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by andymiller6891 on 2009-09-29
im having a problem with installing ubuntu server 9.04.
 
it gets to partitioning, picks up my sata raid but comes up with a geometry error when i try and partition.
 
i have cleaned the drives off before install so there are no existing windows partitions etc.
 
im trying to run a vm server and esxi doesnt like software raid either.
 
anyone know a way roundd installing to software raid??

---

### Post by dstew on 2009-09-29
At present, I think Ubuntu does not support installing to a "FakeRAID", only to software RAID. See this [How-To]("https://help.ubuntu.com/community/FakeRaidHowto") for information on attempts to install to a FakeRAID. Sometimes it works, sometimes it doesn't.

---

