---
title: "Need help with gparted issue on ext3 partion"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by nicoloks on 2009-03-04
Hi All,

Have MythBuntu 8.10 installed on a 250GB HDD (it is the only os installed), and have a new 1TB drive which I am wanting to transfer my entire system to.

I have tried using ddrescue and CloneZilla which seem to go through ok, but end up with the same result. Booting from a live CD and loading up gparted with swapoff I can see my main ext3 partition (in addition to much smaller extended and swap partitions created by the MythBuntu installer), however when resizing I only have the option to shrink the ext3 partition where as I want enlarge it to utilise all the extra storage space.

Why is it that I can enlarge the extended and swap partitions to utilise all the unallocated space, where I am unable to get my main ext3 partition to use it at all? What am I missing?

Really appreciate some help as it has taken me weeks to get my Mythbuntu box all set up, and the thought of having to do it all again to get the partitioning right is almost enough to make a grown man cry.

---

### Post by logos34 on 2009-03-04
sounds like the extended partition containing the swap comes AFTER (second) the ext3 / partition--in other words, it's blocking the way.  Try deleting the swap and making a new one at the END of the disk, then grow / to take up all the intervening unallocated space.  Just remember to edit fstab accordingly afterward

---

### Post by nicoloks on 2009-03-04
Thanks logos34, your answer was spot on. When looking at the graphical display I thought that was what it looked like (extended/swap blocking the extension of my ext3 partition), the I told myself to stop thinking like a windows user. Think it was a case of tricking myself into thinking gparted was more complicated to use than it actually is.

---

