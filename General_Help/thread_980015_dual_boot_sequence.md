---
title: "dual boot sequence"
date: 2008-11-12
forum: General Help
---

### Post by texas.chef94 on 2008-11-12
Circumstances placed me in a position to have to reinstall XP on what had been A HD w/o windows. I had 2 bootable Linux OS.
Now obviously windows resides at hda1.
For reasons that are too involved I now want to reload those 2 Linux OS in what will be a multi boot I guess. The concern I have is the sequence. I want windows to be last in the sequence.
Can someone please direct me to this information or give it to me here. While I have your attention might I ask also is it best to create this partitioning before the fact with gparted or allow ubuntu 8.10 to do it in manual

Thanks

Allen

---

### Post by Elfy on 2008-11-12
> I want windows to be last in the sequence.By this I assume you mean last in the menu list - it will be :)

Assuming that ypou are now in a position where windows is the only os installed and that it is greedily taking the whole drive I would proceed thus

Yes I would deall with the partitioniung before I started any installs

Resize the drive allowing windows it's space.

Create an extended partition with the unallocated space that has appeared.

Inside the extended partition a logical and format that to linux-swap.

Create an ext3 partition for linux1 install
Create an ext3 partition for linux2 install
If needed create a partiton to share data among os's

I would then install the 2 linux os - the last one would install it's grub and make entries for the others.

---

