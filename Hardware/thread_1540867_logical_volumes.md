---
title: "logical volumes"
date: 2010-07-28
forum: Hardware
---

### Post by elfnet on 2010-07-28
Hello!
 
I am a newbie in the linux world so please bare with me and sorry for the terminologies I am using. 
 
Now to my issue, last night I was trying to setup LVM (Logical Volume Manager) and I have initialized 3 partitions from my single drive using pvcreate. These are the commands I used:
 
pvcreate /dev/sdb6 [partition 1]
pvcreate /dev/sdb7 [partition 2]
pvcreate /dev/sdb8 [partition 3]
 
Then, I created a Group Volume to associate the physical volumes (PV). Everything was created fine. Until I realized that I don't see my existing files anymore. All of those partitions /dev/sdb6, /dev/sdb7, /dev/sdb8 have files in them and I need to access them. After I did made them part of the LVM, I can't see them anymore. I hope I did not lose them in the process of make them part of LVM.
 
Now, what I want to do is restore back everything to where it was before. What I did so far is I removed the Volume Group. Now when I look in GParted, I see the 3 partitions but they have LVM beside them. I tried to mount them but they won't get mounted because of LVM. 
 
Is there away to restore my partitions back to the original where I can access my files as how it was before LVM.
 
Let me know if you have any questions.
 
Thanks in advance for your help.
elfnet

---

### Post by IcarusR on 2010-07-28
You may be able to use testdisk to get data back.

[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

I would suggest imaging the drive before you do anything, then if it goes west at least you still have the origional.

You now know the value of doing backups !!

---

