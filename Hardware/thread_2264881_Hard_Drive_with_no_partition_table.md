---
title: "Hard Drive with no partition table"
date: 2015-02-10
forum: Hardware
---

### Post by raffael-azevedo on 2015-02-10
Hi everyone! I have an issue and i'm only posting because i couldn't find the answer on previous topics. So let's go:

I had an issue with a hard drive of an old PC from my aunt. Someone was carrying the notebook and (i don't know how) the disk suddenly stop working properly. She uses Windows. Well, the thing is: i removed the HDD from the notebook and plugged-in with an tool as an external USB hard drive (as i do with other HDDs). The problem starts when the system does not recognize the partition. Using the command[FONT=courier new]lsblk[/FONT] [FONT=verdana]listed all disks and it was there, on /dev/sdc1. The HDD was functioning, but i couldn't access its content. When used GParted, shows only "unaloccated space", but still there, despite this message. I tried everything: TestDisk, [FONT=courier new]ntfsfix[FONT=verdana], but nothing could solve the problem, that was: **can i access the files within the HDD? if i create another partition table (and how do i do this) i lost the content of HDD? There's any hope to recover the data? **

Appreciate all that read. I hope i can find an answer! 
Thanks in advance and sorry about the english.

Raffael.
[/FONT][/FONT][/FONT]

---

### Post by Mark Phelps on 2015-02-11
Using ntfsfix to repair an NTFS partition is essentially a waste of time, as all it does is flag it as "dirty" so the next time Windows starts, it will run a CHKDSK on that partition.

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to use a Windows data recovery app such as "recuva".  But to do that, you would need to be able to remove the drive from your PC, connect it to a working Windows PC, download and install "recuva" -- and run that.

---

