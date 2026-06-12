---
title: "Help me understand RAID"
date: 2010-02-03
forum: Hardware
---

### Post by AmbiguousOutlier on 2010-02-03
I'm new to RAID setups and just trying to get my head round it all. From what I've read this is how I understand RAID 5 v RAID 10 

[IMG]http://img695.imageshack.us/img695/5108/raid.png[/IMG]

So lets assume we have a block of data 6mb in size, lets also assume for arguments sake That 1mb takes 1 sec to write. Let us also assume we have four disks in each setup. 

Therefore have I got this right;

In Raid 5 the first block gets stripped into 3x 2mb blocks and written in the above case to sda sdb sdc. Then the total 6mb block gets written to sdd for parity. So to completely write 1 block takes 6 seconds and takes up a total of 12mb. Block 2 is then stripped across sda sdb and sdd with sdc holding the full parity. I assuming block 2 can be written before block 1 has finished writing to sdd? After 4 blocks have been written we have used a total of 48mb of hdd space to store 24mb of data in 12 seconds.

In Raid 10 the first block gets stripped into 2x 3mb blocks over sda and sdb with a mirror of equal size on sdc and sdd. This process takes 3 seconds. Therefore after 4 blocks have been written we have again used 48mb of hdd space for 24mb of data again in 12 seconds.

Now in both setups one disk can fail without any issues. Although if 2 disks fail in raid 10 then as long as its not the same stripped data we don't lose our data. There is a 33% chance of complete data loss if 2 disk fail.

However in Raid 5 if 2 disks fail then there is a 100% chance of complete data loss. 

I can see no advantage of Raid 5 over Raid 10 only disadvantages. So why do so many people use Raid 5? Have I misunderstood something?

---

### Post by estyles on 2010-02-03
> **RhysGM said:**
> 
In Raid 5 the first block gets stripped into 3x 2mb blocks and written in the above case to sda sdb sdc. Then the total 6mb block gets written to sdd for parity.

I'm no expert, but I can tell you this is not how parity bits work.  You don't rewrite the entire 6mb block to sdd, you only write parity data.  The parity data is only as large as each individual chunk and is used to reconstruct that chunk in the event that it's lost (if the parity data is lost, then you haven't lose any actual information).  So in your example, the parity block is 2mb, same as the other blocks.

> I can see no advantage of Raid 5 over Raid 10 only disadvantages. So why do so many people use Raid 5? Have I misunderstood something?

In Raid 10, you lose half the capacity of the array.  In Raid 5, you only lose the capacity of 1 disk.  So, say you have 10 disks and all are 100GB.  In Raid 10, you only have 500GB of storage space.  In Raid 5, you have 900 GB.

Because of the possibility of losing data in Raid 5 if two disks go out, many people use a hot spare, or use Raid 6, which loses the capacity of 2 disks in order to have 2 parity blocks.

---

### Post by AmbiguousOutlier on 2010-02-04
Thanks for your response, but...

> **estyles said:**
> I'm no expert, but I can tell you this is not how parity bits work.  You don't rewrite the entire 6mb block to sdd, you only write parity data.  The parity data is only as large as each individual chunk and is used to reconstruct that chunk in the event that it's lost (if the parity data is lost, then you haven't lose any actual information).  So in your example, the parity block is 2mb, same as the other blocks.

If that is the case in a 4 disk setup you're only backing up a third of your data. What use is that?

> **estyles said:**
> In Raid 10, you lose half the capacity of the array.  In Raid 5, you only lose the capacity of 1 disk.  So, say you have 10 disks and all are 100GB.  In Raid 10, you only have 500GB of storage space.  In Raid 5, you have 900 GB.

Logically if I have 900gb of data and I want it backed up I will need 1800gb of storage. So how can I fit 900gb of data into 1000gb of storage space?

---

### Post by estyles on 2010-02-05
> **RhysGM said:**
> Thanks for your response, but...
If that is the case in a 4 disk setup you're only backing up a third of your data. What use is that?

I don't think you understand what the parity block is for.  Lets illustrate on a bit level.

Let's say my data is 1010 0111 1011
Let's say we are using 4-bit blocks (thus the way that the data is separated), and lets say we are using a bitwise XOR for the parity function.

Thus we write 1010 to the first drive, 0111 to the second drive, and 1011 to the third drive.  To the fourth drive, we write 0110.  That is the parity data.

How do we get 0110?  Well, for the first bit, it is 1^0^1 = 0.  For the second bit it is, 0^1^0 = 1.  Third is 1^1^1 = 1.  Fourth is 0^1^1 = 0.

Now say we lose the fourth drive.  No problem.  The fourth drive doesn't contain any data (edit: well, it contains parity data - what I mean is that it's not information in the sense that it is just a hash of the "real data"...  note in a RAID 5, the "parity drive" is distributed, meaning the parity block for any block of data can be on any drive, but still any 1 drive can always be rebuilt from the info on the other drives...  having distributed parity improves performance).  We can rebuild it from the other 3.  What if we lose the second drive?  Well, then we have 1010^????^1011 = 0110.  Again, we can rebuild it using the other 2 blocks and the parity block.  Because 1^?^1 = 0, we know ? must be 0.  Similarly for the other bits.

What if we lose drives 1 and 2?  Well, then we have ????^????^1011 = 0110, and we're screwed, because there are many different ways the data could exist to give us that value.  We can no longer replicate data -- we have lost data.

Most of the time, when one drive goes, another drive does not die so fast that you cannot replace the lost drive.  For extremely mission-critical data where you fear the loss of more than one drive, you must go with a RAID 6, or a combination of RAID levels like RAID 10 or RAID 0+1.  (edit: another means of increasing reliability is actually to use drives from different manufacturers, with the assumption that drives from the same batch might fail at around the same time, whereas different manufacturers' drives should fail at completely uncorrelated times.  Also note that no RAID configuration is a true substitute for taking running backups - if data backup is extremely important, you should keep running backups in addition to whatever RAID setup you decide to use...  the old mantra holds "You can never have too many backups.")


> Logically if I have 900gb of data and I want it backed up I will need 1800gb of storage. So how can I fit 900gb of data into 1000gb of storage space?

Because you are not backing it all up.  You are simply using a function to give yourself the ability to recover from a certain amount of data loss.  If you backup all of the data, then you could lose half of it (as long as you don't lose 2 copies any one piece of data) and are fine.  In a RAID 5, you can only lose 1 drive safely.  On the plus side, you only give up 1 drive worth of free space.

---

### Post by AmbiguousOutlier on 2010-02-05
Thank you for that explanation. You've made it very clear.:P

---

