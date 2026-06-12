---
title: "Unable to repair/re-install ubunt svr ubuntu 8.04/8.10 on RAID 5 LVM"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by louis_puttick on 2008-12-03
I wanted to say thanks t all of the posts/tutorials and guides I have used to give me a few years of happiness in using ubuntu.

I have made a bit of a mistake I believe which has left me with a problem....

I have a HP xw4300 with 4 sata disks and 1 ide disk. The 4 sata disks are in a RAID 5 set with 1 LVM. The LVM is for Home and spare space on the sata disks in various stripes or mirrors is used for swap,var and tmp. On the IDE there is root, boot and USR.

I previously broke the IDE disk and replaced it and on installing 8.04 was able to identify Home, swap, var & tmp and rebuild the new disk and all was well.

Recently I wished to try KDE 4.1 whish did not go well and on removal it got even worse mainly through me tinkering with bits of debian I did not completely understand. So I thought I would move to ubuntu 8.10 svr and so re-installed the ide disk. It did not see the LVM but I though I would be able to see it once the build completed and I got a GUI to work with. I was wrong, and on the subsequent re-install of 8.04 and being able to see the LVM and set home, swap, var & tmp when the machine re-booted it cannot write to any of the sata disks and therefore will not boot beyond grub.

Is there any way I can re-install a sever OS with a gui and re-mount the LVM happily?

Many thanks in advance for reading through this and for any comments you have.

---

### Post by louis_puttick on 2008-12-06
bump

---

