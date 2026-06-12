---
title: "Something i would like to do"
date: 2008-10-20
forum: General Help
---

### Post by Monotoko on 2008-10-20
Hiya, im currently running a duel-boot with windows XP and Ubuntu, my current partition table is as follows:

Partition1(sda1): Ubuntu (Not lettered in Windows) - 10GB
Partition2(sda3): XP (C:\) - 10GB
Partition3(sda4): SharedFiles (S:\) - 220GB

Both Ubuntu and XP have access to the shared files partition.

XP is already set up to do what i want, in a way, as the My Documents folder is targetted as S:\MyDocs

I was wondering if it would be possible to make my home directry also lead to that partition, that way, both the home directry from ubuntu and the My Documents folder from windows, is on the same partition, so if one ever dies, i can easily get my stuff.

---

### Post by bodhi.zazen on 2008-10-20
yes you can do this. I would mount is as a data partition an not /home.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

