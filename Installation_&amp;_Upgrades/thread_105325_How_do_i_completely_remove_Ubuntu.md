---
title: "How do i completely remove Ubuntu?"
date: 2005-12-18
forum: Installation &amp; Upgrades
---

### Post by Russell on 2005-12-18
I've enjoyed using Ubuntu but need to install XP again.

I've tried several things to completely remove Ubuntu but nothing appears to work. The Windows system disk wont boot, theres no utilities allowing me to format on the Ubuntu installation CD

I've tried to create a Windows98 bootdisk so that i can use fdisk but haven't been able to do it.

Could someone give me some advice please? thanks alot!

---

### Post by daschl on 2005-12-18
if you wish to remove the partitions created by ubuntu you could do so :)

insert the windows xp cd and with the built-in-hdd-tool you can remove the partitions and install the operating system

(but remember: this is a ubuntu support forum, so for windows-related stuff this is maybe not the right place ;))

but maybe if you can give us more informations we can solve the problem together

---

### Post by Russell on 2005-12-18
I did have my reservations about posting this on the site. Don't get me wrong, installing XP is out of neccessity and no real desire of my own. If i had my way, i'd never go back to it.

I've tried to load the "factory reset" CD but it won't boot, which is odd considering that the Ubuntu CD will. I don't know what to do next.

---

### Post by Russell on 2005-12-18
The windows disk does boot, however an error message comes up and it exits. It says something along the lines of

Drive imagine special edition partition not found. Program is now exiting.

any ideas?

---

### Post by ubuntu_demon on 2005-12-18
I moved this thread.

---

### Post by daschl on 2005-12-18
do you have a "normal" installation cd or one of these freaky-recovery cds (i had them on my laptop too :rolleyes:)

because maybe it searches for the old windows partitions (windows is unable to identify the ext2/3, reiser,.. partitions)

try to boot the ubuntu live-cd or knoppix and create "normal" partitions, which windows is able to read.

or you can erase the complete disk and try it again. i think you have to play around a lot, i'm sorry that i cant tell you exactly what to do.

---

### Post by encho on 2005-12-21
I think that recovery disk won't help. You need 'regular' XP CD.
What happened is that some pc companies, like Dell for example, create special partition on primary hard drive which contains recovery tools and drivers. Your rescue cd was 'expecting' to find such a partition, but failed to do so as you probably deleted it when choosing 'use complete hard drive' during ubuntu setup.
So find or borrow XP CD and go ahead.
Sorry to see u live.

---

