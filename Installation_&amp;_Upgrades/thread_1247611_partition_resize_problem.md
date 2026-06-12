---
title: "partition resize problem"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by maksimpiriyev on 2009-08-23
i installed ubuntu, i have 4 primary partition.
i want to extend the partition which is ubuntu installed,but in gparted resize is not active for that partition.
also it says you can't create more than 4 primary partition,when i want create new one

---

### Post by Partyboi2 on 2009-08-23
Hi, you can only have 4 primary partitions, so if you are wanting to create more partitions you would need to create a extended partition, but to do this you would need to remove one of your 4 primary partitions.

---

### Post by Bartender on 2009-08-23
I'm surprised you got a fourth primary on there.  I've had the Ubuntu installer and GParted LiveCD balk at doing that.  

What exactly are on those four primaries?  If one is a recovery partition, and you've already burned recovery discs (you _have_ burned your recovery discs, right?) you could delete the recovery partition.

Another option is saving your important personal data from the Ubuntu partition to some external device, deleting the Ubuntu partition, creating an extended partition, and reinstalling Ubuntu inside the extended.  If you do this, Windows will not work until you've reinstalled Ubuntu because of the GRUB/MBR thing.

If it were me, I'd do both.  Get rid of the recovery partition, move or resize to take advantage of the freed space, and reinstall Ubuntu to an extended partition.

---

### Post by AmerNewbieInDE on 2009-08-23
> **maksimpiriyev said:**
> i installed ubuntu, i have 4 primary partition.
i want to extend the partition which is ubuntu installed,but in gparted resize is not active for that partition.
also it says you can't create more than 4 primary partition,when i want create new one

the partition is mounted, thats why it is locked.. boot with a live cd and run gparted from there.

---

### Post by raymondh on 2009-08-23
> **Bartender said:**
> 
 If one is a recovery partition, and you've already burned recovery discs (you _have_ burned your recovery discs, right?) you could delete the recovery partition.


Some OEM installs require a recovery partition as well as a recovery disc to do any type of recovery.  Better to suggest that OP should check with manufacturer documentation first.  

@ OP .....

Can you boot into the liveCD, > go into live session (TRY UBUNTU .... ) > access gparted (system > admin > partition editor ) 

-   It will pull up a visual of your HD
-   Take a screenshot  (press prtscr) and save it to your desktop

On your next post, click attach (and a new window pops up) > browse to your desktop and open the gparted screenshot > import

That'll give the forum a visual guide.

You can only have 4 primary partitions (or 3 primary + 1 extended).  Ubuntu does not care if it is in a primary partition or not.

---

