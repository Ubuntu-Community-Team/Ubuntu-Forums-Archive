---
title: "converting NVRaid stripe to mirror with dmraid"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by jomex on 2009-07-27
hello!

i want to use Ubuntu and Windows together on one disk with a NVRaid RAID
what i did so far was creating a stripe array in BIOS with only one HD. i successfully installed Ubuntu on it and it works fine. now i want to add the second HD and convert the stripe to a mirror.
how do i do that (dmraid)?

---

### Post by ronparent on 2009-07-29
Yes, dmraid would be your choice if you want to access your drives with both ubuntu and windows. Your conversion would be done in bios as was your original raid0 setup. Be aware that the process would entail rewritting the partition tables of your current drive and loss of all data on it. Anything of value should be backed-up before proceeding.

---

