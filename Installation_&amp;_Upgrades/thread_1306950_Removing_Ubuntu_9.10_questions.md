---
title: "Removing Ubuntu 9.10 questions"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by 3DGE on 2009-10-30
I have installed Ubuntu 9.10 and after a lot of time and troubleshooting I just don't want to have it installed as a full OS just yet, I will probably just run it in VirtualBox again or maybe Wubi. 

But my question now is I installed it along windows not using Wubi and installed it onto a partition inside my main harddrive which is my E drive. (I have 4 partitions in my 1 hard drive - C,D,E,F)
Now I want to get rid of Ubuntu and so I right clicked My Computer and went to Storage and now I see the NTFS that is still part of windows and there is 2 partitions one is the size I have to Ubuntu and there is another one that is 1.56GB which are both Unknown Partitions.

It would make sense to me if there were only 2 partitions inside my E drive which would mean E for windows and E for ubuntu but this third smaller one is confusing me is it also part of Ubuntu?

And also if I want to get rid of it now do I go to delete logical drive for them and then format them again to get the space back for windows or will I need to reformat all of the E drive?

I really just don't want to mess anything up when trying to get rid of this, another quick question do I have to do anything special to get rid of the dual boot screen where I pick between between Ubuntu or Windows. Or when I reformat the partition that Ubuntu was on it, will it get rid of it.

---

### Post by phillw on 2009-10-30
> **3DGE said:**
> I have installed Ubuntu 9.10 and after a lot of time and troubleshooting I just don't want to have it installed as a full OS just yet, I will probably just run it in VirtualBox again or maybe Wubi. 

But my question now is I installed it along windows not using Wubi and installed it onto a partition inside my main harddrive which is my E drive. (I have 4 partitions in my 1 hard drive - C,D,E,F)
Now I want to get rid of Ubuntu and so I right clicked My Computer and went to Storage and now I see the NTFS that is still part of windows and there is 2 partitions one is the size I have to Ubuntu and there is another one that is 1.56GB which are both Unknown Partitions.

It would make sense to me if there were only 2 partitions inside my E drive which would mean E for windows and E for ubuntu but this third smaller one is confusing me is it also part of Ubuntu?

And also if I want to get rid of it now do I go to delete logical drive for them and then format them again to get the space back for windows or will I need to reformat all of the E drive?

I really just don't want to mess anything up when trying to get rid of this, another quick question do I have to do anything special to get rid of the dual boot screen where I pick between between Ubuntu or Windows. Or when I reformat the partition that Ubuntu was on it will get rid of it.


that's one heck of a lot a questions ... and scenarios ...

I'm suprised that you would 'leap' into 9.10 as your 1st foray into ubuntu - I'd have recommended 9.04 for interaction with windows.

Can I narrow it down a bit ?

1) Windows 100% of disk with no ubuntu
2) Windows with wubi
3) Windows with a ubuntu partiton

Now, 3, is dual boot - but it can be set to default to windows - having a linux partition does have it's own little advantages ... a nice safe place, so that, heavens forbid, a nasty got onto & into your windows system, you'd have a safe area to recover data into.  I think, from memory, dell are using something like this for their rescue partition, but I could be wrong.

Decide what you want & we can sort out some instructions for you.

---

### Post by 3DGE on 2009-10-30
Well right now I just want to remove Ubuntu from my system completely and get rid of dual boot so I only boot into Windows for now.

Also I had Ubuntu 8.04 on my old computer and loved it, but I have a new computer so I wanted to get Ubuntu up and running again.

---

### Post by 3DGE on 2009-10-30
Anybody?

---

### Post by connorh123 on 2009-10-30
Just dual-boot.

---

### Post by skyiscrying on 2009-10-30
Is there a DiskManagement tool? I recall, well I think, that XP had one, and from there you could delete partitions - if that is what you want to do. Save what you want before you start to fiddle around.

---

### Post by 3DGE on 2009-10-31
Alright well I figured it out. 

I had to install a program called MbrFix and run some some commands in windows to get rid of the dual boot, then I used Paragon partition manager to remove the allocated space for Ubuntu and then used it again to merge back that space onto my other Windows Partition.

---

