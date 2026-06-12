---
title: "Problem viewing paritions with wubi xubuntu"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by mlorette on 2009-04-01
hello!

i installed xubuntu in vista today using wubi. i have done this many times with ubuntu, and once with kubuntu, and they never gave me this problem. the issue is, my hard drive has 2 partitions, recognized as separate drives. the C: where i have windows and xubuntu, and the D: which has my files. when i boot into xubuntu, in my places menu and file browser i only have access to the c drive via the "host" folder... no access to d which normally appears as a removable hdd.
can anyone tell me how to get to my d drive  (it doesnt show up anywhere) without formatting anything?:confused:

---

### Post by 123456789123456789123456 on 2009-04-01
> **mlorette said:**
> hello!

i installed xubuntu in vista today using wubi. i have done this many times with ubuntu, and once with kubuntu, and they never gave me this problem. the issue is, my hard drive has 2 partitions, recognized as separate drives. the C: where i have windows and xubuntu, and the D: which has my files. when i boot into xubuntu, in my places menu and file browser i only have access to the c drive via the "host" folder... no access to d which normally appears as a removable hdd.
can anyone tell me how to get to my d drive  (it doesnt show up anywhere) without formatting anything?:confused:

interesting, what format is the d: in?
From what I understand of Wubi, it is up to windows to inform ubuntu about the hardware and partitions on the computer.  If windows did not inform xubuntu that the d: was there, it would probably not be able to reconize it.  easy test, take a copy of the live cd, boot into the live cd, and see if the live cd reads the partitons.  If so, for some reason, windows did not inform xubuntu.  you can see if the gparted or other disk management software on the ubuntu installation reads that the disk is there.

if it does read the partition was existing, make note of the disk location, and try the mount command in terminal to mount the drive.

---

