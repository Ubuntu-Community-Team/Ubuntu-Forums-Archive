---
title: "Possible RAID Configuration (0's and 1's)"
date: 2011-08-25
forum: Hardware
---

### Post by Icculus on 2011-08-25
I have just built a new computer that has a 320G HDD (call it Drive 1) and two 1.5T HDDs (Drives 2 and 3). 

Drive 1 is used to run OSes. I have Ubuntu and 7 on it.

Drives 2-3 are going to be implemented as a RAID 1 to help in case of drive failure (which has already happened once)

I just got to thinking: Is it possible, preferably through hardware on my mobo, to create a partition on drives 2-3 that would create a RAID with drive 1?

The end result would be a RAID 0 between drive 1 and drives 2+3. Drives 2 and 3 would be identical. Therefore, if I lost drive 1 I would still lose the OSes (which is currently the case), if I lost drive 2 or 3 I wouldn't lose anything, and if I lost drives 2 and 3 the world would crush in upon itself.

Could there also be a parity (RAID 5) across partitions of the three disks?

---

### Post by b0b138 on 2011-08-25
You could mirror (raid 1) drives 2 and 3 and keep all your data there. You can partition it however you want, say 1 part for ubuntu, 1 for win and 1 thats shared. Or one big part that both os's can see.

Personally, I think raid is over complicated and overrated for home use. If it were me, I would use drive 2 for all my data and use drive 3 for backup use. And if your big drives have room, you could use a utility to make up an image of drive one.  That way if drive 1 does die, you can replace it and then just reimage.

---

### Post by sanderd17 on 2011-08-25
> **b0b138 said:**
> 

Personally, I think raid is over complicated and overrated for home use. If it were me, I would use drive 2 for all my data and use drive 3 for backup use. And if your big drives have room, you could use a utility to make up an image of drive one.  That way if drive 1 does die, you can replace it and then just reimage.

+1

The advantage of working with backups is that you can go back into the past. If it happens that you deleted something you didn't want to delete, you can recover it with backups, but on RAID1, it will be gone.

The only advantage of RAID1 is that it doesn't take time to repair, the server can be running while repairing.

Oh, and there is no reason to use RAID0 (and probably dangerous) for the OS and data disks together.

---

### Post by cbowman57 on 2011-08-25
I'm running an installation using software RAID0, it was a bit complicated to get setup & running but the speed is great.  It does bring with it a whole slew of new challenges though, about the only backup option is tar.  My favorite, Clonezilla was rendered useless.

If I had 3 drives I probably try RAID0+1 (RAID10?) for speed & redundancy.

Don't expect to find a lot of simple guides on how to get it running though. :)

---

### Post by sanderd17 on 2011-08-25
RAID0 is also called "stripping" right? So that means it divides the data between the different disks in the RAID.

So it will put your data in both, your OS disk and your data disks. And it will also put your OS in both disks.

This will give a speed advantage, but if the first disk fails, having the other two disks in RAID1 won't help you a bit since half of your data is on the crashed disk.

If you want to use RAID1+0, than you have to use at least 4 disks.

And the RAID1 config for the data disks won't give you any speed advantage, and there are better backup methods (since a desktop may be rebooted and may be down for some hours, restoring a backup).

---

### Post by sanderd17 on 2011-08-25
Maybe you could use RAID0 between the OS disk and one data disk. And use your third disk to make tar backups.

This way, you have the speed advantage of RAID0, and you have backups.

---

### Post by cbowman57 on 2011-08-25
> **sanderd17 said:**
> RAID0 is also called "stripping" right? So that means it divides the data between the different disks in the RAID.

So it will put your data in both, your OS disk and your data disks. And it will also put your OS in both disks.

This will give a speed advantage, but if the first disk fails, having the other two disks in RAID1 won't help you a bit since half of your data is on the crashed disk.

If you want to use RAID1+0, than you have to use at least 4 disks.

And the RAID1 config for the data disks won't give you any speed advantage, and there are better backup methods (since a desktop may be rebooted and may be down for some hours, restoring a backup).

Exactly right, it provides no redundancy.  I do it purely for the speed & use alternate backup methods, as well as keeping my important partitions on non-RAID partitions.

Using my computer at home is for fun, I don't do anything mission critical so the gain in performance is worth more to me than data security.

With the RAID that some motherboards come with I think you have to create the array with the entire disks.  Linux software RAID allows you to assemble arrays using partitions, that's the way I understand it, I could easily be wrong.

---

### Post by Icculus on 2011-08-31
I'm sorry for the seeming 'one-and-done' status of this post. I'll have to verify my settings that I get email notifications when comments are made.

I tried doing a RAID through my Mobo. Everything got kinda fubared... but that's for another topic.


After seeing the comments (and being unsuccessful on the RAID setup) it doesn't seem like I can mirror my two media drives in a simple manner, especially given the fact that I double boot into W7.

So... I think I'll research some sort of incremental backup solution through Windows and/or Linux to try to help backup my schtuff.  I am under the impression that if it were a "true" RAID controller it might just work marvelously, but in the meantime I am left with two empty 1.5T drives that aren't reading in Ubuntu and a Windows 7 installation that blue screens on boot.

---

### Post by gpost3 on 2011-08-31
Some people use their home computer for nothing more than gaming or  surfing the net. I use my home computer for important work as well as  for gaming so data security is somewhat important to me. 

Your unsuccessful attempt with raid doesn't necessarily mean raid is bad and I'm not sure what you mean by "True Raid Controller" and "Work marvesouly". Any piece of hardware needs proper configuration and necessary software to go with it.

And Hang on to final verdict OP. You have quite a few options here with your two 1.5 TB and 320 GB. First you need to break down the type of data you have to work with. I think we have four categories:

A - System Data : Your OS and system files
B - Configuration Data: Your User Profile in Windows and your /etc folder in Ubuntu
C - Personal Data (Critical): Your documents, pictures, memories, audio recordings
D - Personal Data (Non-Critical): Stuff that you download off the internet which you can **easily **download again if you were to lose it

I would keep an incremental backup of C for sure and possibly B as well. I personally wouldn't care for A and D but some people like to keep an image of A. I like the simplicity of two hard drives. I would keep say a fast 500 GB as my main and store A, B and C on it and a 2 TB as my backup/data and store B, C and D on it. This way you have A, B', C' and D where ' indicates additional copies serving as backups. Since you have the disks, you can try and play around with mdadm. I have used it with a good success before on Ubuntu. Windows has dynamic disks which can create a stripped partition for you so it works at partition level. You can use rsync to create incremental backups using Ubuntu. Also there is BackupPC which uses rsync as its engine to create automated incremental backups. It can be a bit tricky to configure though but nothing that is out of my scope to help you with.

---

### Post by gpost3 on 2011-08-31
My Ubuntu loads pretty fast without Raid0 so I personally don't feel the need to make it load any faster but if anything - I feel I could use Raid0 for Windows Boot partition.

---

