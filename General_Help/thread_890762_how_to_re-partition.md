---
title: "how to re-partition"
date: 2008-08-15
forum: General Help
---

### Post by jsalas8 on 2008-08-15
it seems i was a little confused during the installation process when it came to partitioning and i only left my windows with about 1 gb space and gave the rest to linux. how can i re-partition my hard drive?

---

### Post by BarryMaccaukner on 2008-08-15
You can use gparted or qtparted ...you may have to install them from synaptic, but you can check by opening a terminal and typing gparted or qtparted. Then you can resize. Both of those partition editors are similar to partition magic

---

### Post by RATM_Owns on 2008-08-15
Boot into your Ubuntu Live CD and at the top left, click System->Administration->Partition Editor and you can edit everything from there.

/dev/sda1 will usually be your Windows partition. So /dev/sda2 should be your Ubuntu partition.
Just right click /dev/sda2 and choose Resize/Grow. You want to open up space in front of your Ubuntu partition so you can easily add it to Windows. Then right click /dev/sda1 and choose Resize/Grow and add the extra space to Windows.

It will not work when you're booted into Ubuntu on your hard drive because the drives can't be mounted. And it would be stupid to unmount the drive you're currently using.

---

