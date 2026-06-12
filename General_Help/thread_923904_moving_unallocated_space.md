---
title: "moving unallocated space"
date: 2008-09-18
forum: General Help
---

### Post by twitch2197 on 2008-09-18
is there ANY way to move unallocated space into the extended partition my linux installation is in? if so, what program can i use, or what terminal commands do i use?

---

### Post by plucky on 2008-09-19
> **twitch2197 said:**
> is there ANY way to move unallocated space into the extended partition my linux installation is in? if so, what program can i use, or what terminal commands do i use?

You cannot move unallocated space,but you can resize the extended partition to include the unallocated space provided the space is adjacent to the partition.

You can use the partition editor on the Live CD or download and burn a Gparted Live CD from[here.](http://gparted.sourceforge.net/)(Very useful tool in your computer toolkit.)

The Gparted partition editor can also be used to move partitions.

After you have resized the extended partition to include the unallocated space,you can then move and resize the logical partitions within the extended partition.

Remember, you cannot resize or move partitions that are mounted,that is why it is probably best to use  a Live CD.

Moving partitions can take a long time as it has to move the data as well,so try to be patient when doing so and not stop it before it has finished.

[color=blue]It is recommended that you have backups of your important files before doing any partitioning,so that you can recover your data in case something goes wrong.[/color]

Good Luck

---

