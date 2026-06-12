---
title: "SSD is nearly full, possible partition error"
date: 2014-07-18
forum: Hardware
---

### Post by uaebuntu on 2014-07-18
Using 32 bit Ubuntu 14.04, the disk is a 128GB SSD which I try and keep  no more than 50% full for perfomance reasons However looking at the disk analysis it seems I have used about all of the available 121 GB.  I looked to see which files and users were taking up space and remove a few files and best I could get it down to was 93GB (see attached file). I would have expeceted about 40 GB, which was backed up by looking at computer properties (attached) where in fact it was about 33GB. So there is 60 GB of the disk being used by something. Ran fdisk and it seems there is a partition error, how do I fix it? Could this be the cause of the lost space.[ATTACH=CONFIG]254805[/ATTACH][ATTACH=CONFIG]254806[/ATTACH][ATTACH=CONFIG]254807[/ATTACH]

---

### Post by TheFu on 2014-07-18
You are using LVM.  Check out commands specific to LVM to see where the storage is allocated and how much is free. lvdisplay and vgdisplay should get you started.

---

### Post by uaebuntu on 2014-07-18
Thanks TheFu,

It has left me more confused though. I looked up about LVM and can't say I understand it all, but at least it gives me something new to learn. I ran the commands you suggested, but not sure what they are telling me.
[ATTACH=CONFIG]254825[/ATTACH][ATTACH=CONFIG]254826[/ATTACH]

The way I read it I have a physical and logical volume of 120GB

When I run df then it says 88 GB of that is used, yet I still believe it should be about 33GB as per my earlier post. So I don't have a partition error but I still have 55 GB of "ghost data on the volume and I don't know how to see what it is and if necessary free up the space.

---

### Post by oldfred on 2014-07-19
I do not use LVM, but it is a logical partition scheme over the top of the physical partitions. So the physical partitions are full of the LVM.

 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

### Post by TheFu on 2014-07-19
sudo du -sh /*

then work your way into every "problem" directory to find which files are eating all the storage.

OR

```
sudo find / -type f -size +500M -print
```
Clean up the biggest files then run the command again with 50% less size option over and over, until you've achieved the desired results.  I bet most of the crap/large files are in your $HOME.  That's where they are on my systems. ;)  If you have network storage attached (cifs/nfs) and don't want to search that, there are options to prevent **find** from traversing those. Sorry - don't recall those off my head now.

---

### Post by uaebuntu on 2014-08-22
Thanks everyone

Got it sorted.. the delay in repling was due to family holidays, almost as much fun as Linux.

Anyhow the reasons behind this were my son had done a restore of his home directory after he broke a game adding a mod. We use simple backup and he got the restore options wrong and we got a whole bunch of hidden *before_restore* files created and then after the next backup he did it again and not only did it restore the old files but we had *before_restore.before_restore* files which explained the sudden increase in capacity.

Learned about LVM, recursive deleting, and find,  as well as getting my SSD space back.

---

### Post by TheFu on 2014-08-22
Any plans to add "quotas"?  Just asking.

---

### Post by uaebuntu on 2014-08-22
My plan was to add a 1TB SATA drive and move the /home directories there, then teach my son how to restore properly (he is 8 in Sept so I'm pretty impressed he got as far as he did anyway)

That way I keep the SSD for boot and system to maintain performance and we have plenty of space for fun.

I have a NAS which people were supposed to keep their non "working" files on and which all the computers are backed up to, but this scheme is cumbersome for the less techy in the house and has this downsidbe of using up the SSD  by accident.

so a TB of workspace, possibly with size rather than file number quotas now you've mentioned it solves a problem. Haven't checked yet but can I over allocate? i.e. everybody has 500 GB although there is only 1 TB in total as some users are less active, or do I just give them smaller quotas?

---

