---
title: "Help Resizing Partition"
date: 2008-07-22
forum: General Help
---

### Post by jaydenop on 2008-07-22
I have windows vista installed an I just installed Ubuntu. Before I installed ubuntu I 50GB free of my 300GB HD. So when I was intalling ubuntu i came to the"prepare disk space" screen and i choose resize SCSI1 and choose 55.6GB. Ubuntu installed successfully but now my windows vista partition is 55.6GB and I think my Ubuntu partition i think is only 45MB? I went into G-Parted(see attached) and there is a partition called ext3 that is 230 GB and G-Parted will not let me resize it. What did i do wrong???

I ultimately would like my ubuntu partition 30 be 50GB and my Vista Partition to be the rest. How can I do this?? Do I need to start over?? 

See Attached file of G-Parted

---

### Post by Dutch70 on 2008-07-22
Looks like you're gonna have to delete the sda4 partition, and extend the windows partition. I recommend doing this from within vista. it doesn't like to messed with by other programs.

1. Right click on Computer
2. Select Manage
3. Click on Disk Management
4. Right click on a partition
5. Select Extend 

As with all changes to partition sizes, have a good set of backups beforehand is a good idea

 Then reinstall ubuntu. unless someone else knows a better way. I dont.
also, my advice is dont be in a big hurry, you may change your mind later.

Dutch

---

### Post by jaydenop on 2008-07-22
I have windows vista installed an I just installed Ubuntu. Before I installed ubuntu I 50GB free of my 300GB HD. So when I was intalling ubuntu i came to the"prepare disk space" screen and i choose resize SCSI1 and choose 55.6GB. Ubuntu installed successfully but now my windows vista partition is 55.6GB and I think my Ubuntu partition i think is only 45MB? I went into G-Parted(see attached) and there is a partition called ext3 that is 230 GB and G-Parted will not let me resize it. What did i do wrong???

I ultimately would like my ubuntu partition 30 be 50GB and my Vista Partition to be the rest. How can I do this?? Do I need to start over??

See Attached file of G-Parted

---

### Post by compnut41 on 2008-07-22
I have been there and feel your pain. What I did was right clicked on the swap partition and chose swapoff, and then I was able to adjust the partition sizes. And keep in mind that vista will sometimes be a little screwy after you resize the partition so back up anything important.

---

### Post by jaydenop on 2008-07-22
i cant delete the sd4 partition. when i go to gparted and click on it all the options for it are greyed out

---

### Post by BGFG on 2008-07-22
If you do indeed reinstall i'd suggest you use the built in vista tool in disk management to partition your drive. Ubuntu should see it on installation.
But like Dutch said, give it some time :) you may well prefer ubuntu with more space after a while.
(not to nudge you in a particular direction or anything)

I'm currently contemplating fragging my vista drive and putting on OpenSolaris.

---

### Post by Rocket2DMn on 2008-07-22
Please do not cross post the same problem on different forums.  We understand that you are having a problem, but double posting creates extra traffic and isn't fair to the users helping you.
Good luck with your partition resizing.  Thanks.

---

### Post by Baelus on 2008-07-22
You'll need to delete the extended partition, the one with swap and the 3G FAT32 partition. Copy anything from the FAT32 partition because it will be wiped.

That will let Gparted resize your EXT3 Ubuntu partition to 50G. You'll have to move the end of the partition in, you can't change the start of the partition.

Once you've pulled it in to 50G you can then move it to the end of the drive, keeping space for the swap and 3G partition you wanted.

Resize your Vista partition to fill the empty space.

Finally, create the swap and 3G partitions in an Extended partition.

So here's the order:

1. Delete Extended and partitions contained within it.

2. Resize EXT3 Ubuntu partition to 50G.

3. Move Ubuntu partition to the end, leaving space for swap, etc.

4. Resize NTFS partition to fill remaining space.

5. Create Extended containing swap, etc.

Do these one at a time, not in one whole shot. This is quite a risky operation, so make sure all your important data is backed up. Whenever you mess with partitions like this, expect to lose everything. That way, when things go right, you're pleasantly surprised. And if they don't, you can rebuild it without too much damage being done.

- B

---

### Post by Dutch70 on 2008-07-22
> **jaydenop said:**
> i cant delete the sd4 partition. when i go to gparted and click on it all the options for it are greyed out

You have to be on the live cd, you cant partition a drive that you have mounted...:)

also I edited my first post... so, in case you haven't noticed. check it again

Good call BGFG, I was editing my first post when you made yours (about doing it from within Vista):)

Dutch

---

### Post by jaydenop on 2008-07-22
Thanks for everyones help I did use some of your ideas but ultimatey I used a program called diskpart. Here is the link that helped me do this:
[http://vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work](http://vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work)

---

### Post by Dutch70 on 2008-07-22
Great, thanks for posting your solution!

Don't forget to mark your thread solved so others can find the solution that you used, with the forum search tool if they need to. :)

Dutch

---

