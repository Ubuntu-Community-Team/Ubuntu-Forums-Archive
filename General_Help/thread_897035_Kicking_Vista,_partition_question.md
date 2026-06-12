---
title: "Kicking Vista, partition question"
date: 2008-08-21
forum: General Help
---

### Post by Inane_Asylum on 2008-08-21
I had Vista/Kubuntu on a dual-boot, and needless to say, using Vista only helped increase my love for Ubuntu exponentially. I killed Vista (on purpose, in cold blood8-)), and now want to have Kubuntu on the entire HDD (with a couple smaller partitions for /home and whatnot), while running XP as a virtual box. Since Kubuntu was installed on the second partition after Vista, will there be any problems merging the partitions, or at least shrinking the Vista partition to put my /home files in?

If not, how would I go about doing it? Messing around with partitions makes me nervous...

---

### Post by ugm6hr on 2008-08-21
**Advice: Backup before messing with partitions.**

That said...

Best solution is to leave Ubuntu where it is (i.e. untouched - hence no need to mess with Grub etc), reformat the Vista partition as ext3 and use it as a separate /home partition.

Instructions here: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

