---
title: "Error: Multiple OS options in Grub"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by kenji_03 on 2009-09-14
So I installed Ubuntu on my vista machine, it took a few installs as trying to mod my partitions without losing data was very tricky.  Along with the fact that Grub didn't like me at first...

However, when I finally did get Ubuntu installed and Grub running without error, I found I had something like 4 Ubuntu and Ubuntu memory check OS installs, with my Vista at the bottom.

Is there any way I can change GRUB so it boots into either Vista first, or so I don't have to scroll through 8 options to get to Vista?

---

### Post by Partyboi2 on 2009-09-14
Hi you can change default by editing your /grub/menu.lst. 
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

To remove some of the older kernels from the grub menu you can open Synaptic (System>Admin>Synatpic) and search for 'linux-image' and remove the older ones, keep your current one and the one before you current one as a backup.
If you have multiple Ubuntu installs (Not referring to kernels listed in grub menu) you can boot a Ubuntu live cd and use gparted (System>Admin>Partition Editor) and delete the ones you don't need.

---

### Post by kenji_03 on 2009-09-20
> **Partyboi2 said:**
> Hi you can change default by editing your /grub/menu.lst. 
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

To remove some of the older kernels from the grub menu you can open Synaptic (System>Admin>Synatpic) and search for 'linux-image' and remove the older ones, keep your current one and the one before you current one as a backup.
If you have multiple Ubuntu installs (Not referring to kernels listed in grub menu) you can boot a Ubuntu live cd and use gparted (System>Admin>Partition Editor) and delete the ones you don't need.

This worked perfectly!  Thank you so much :D!
(On a side note, I also found [this thread]("http://ubuntuforums.org/showthread.php?t=1270887&highlight=boot+options") for anyone else who reads this post)

---

