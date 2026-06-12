---
title: "Misaligned partition"
date: 2011-11-22
forum: Hardware
---

### Post by noeyx on 2011-11-22
Hi, can anyone help me on this (pls. see attachment)? I can't delete the partition using gparted and I've reinstalled Ubuntu 11.10 twice already.

---

### Post by coffeecat on 2011-11-23
> **noeyx said:**
> I can't delete the partition using gparted 

Are you trying to do that from the live CD? If so, that could be because you are trying to delete a swap partition and/or the extended partition in which the logical swap partition resides. In Gparted in the live CD session, right-click on the swap partition and choose "swapoff". That will unlock both sda5, your swap partition and sda2, the extended partition, and you will be able to delete them.

If you are still unable to create a properly aligned partition, post a screenshot of a Gparted window and the output of this terminal command:

```
sudo fdisk -lu
```

---

### Post by noeyx on 2011-11-23
Hi coffeecat, thanks for your reply. I've already used Gparted and done what you've said before I posted in this forum. I've done the swapoff and deleted all the partitions before I installed this OS. Here is the output of sudo fdisk -lu:

---

### Post by noeyx on 2011-11-23
By the way, I've seen a similar problem in another thread. However, I can't understand the explanation by srs5694 who said that partition alignment is "irrelevant: for a 4096-byte physical sector. Here is the link: [http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

### Post by coffeecat on 2011-11-24
> **noeyx said:**
> By the way, I've seen a similar problem in another thread. However, I can't understand the explanation by srs5694 who said that partition alignment is "irrelevant: for a 4096-byte physical sector. Here is the link: [http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

That thread is a good find. I'll quote what srs56945 says in post #8 of that thread because it seems to be directly relevant. srs5694 is an expert on partitioning matters and is worth listening to.

[quote="srs5694"]All of your primary and logical partitions are properly aligned on 2048-sector boundaries, so they're all fine. The extended partition (/dev/sda2) that houses your logical partitions, though, starts just two sectors (1024 KiB) before your first logical partition. Thus, in some sense that partition is 1024 KiB misaligned. That's the value reported by the warning, which makes me think the warning is referring to that partition. This is 100% irrelevant, though. The reason is that the partition alignment matters because of filesystem data structures within partitions; however, filesystem data structures are aligned relative to logical partitions (or primary partitions), not to the extended partition that houses logical partitions. My suspicion is that the program checks for partition alignment but is overzealous and checks the alignment of the extended partition, which it shouldn't be doing. If so, this is a bug.[/quote]

As with the OP of that thread, it is your extended partition that is "misaligned" by 1024 bytes, and as with that thread it is disk utility that is giving you an error. srs5694's 100% irrelevant comment is because an extended partition does not contain a filesystem itself. An extended partition's sole purpose is to act as a container for logical partitions which contain filesystems. Your logical partition (sda5) starts on sector 970625024, which is a multiple of 2048 and therefore correctly aligned.

It seems therefore that all is fine and that you could ignore the disk utility error message. A question: when you deleted all the partitions and then recreated them, which partitioning tool did you use? With Gparted, if you leave the alignment default, it *should* create partitions on correct boundaries.

---

