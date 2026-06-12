---
title: "dual boot XP Ubuntu partitions Acer 751h"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by aspergerian on 2009-10-21
My new Acer 751h (XP, 160g hd) will arrive tomorrow. I have installed, used, and appreciated Hardy Heron on 3 netbooks, including the HP Mini which I use daily. I intend to have my Acer 751h as a true dual boot not via Wubi. 

My plan at this time is to allocate 60 gig to HP, 60 gig to Ubuntu, and (if possible) 40 gig to a partition for data files than can be read by XP and by Ubuntu.  

Question 1: Is the aforementioned 60, 60, 40 doable with the 40 read by both XP and Ubuntu? 

I assume my first step will be to create three partitions in the 160 gig hd. The first partition will remain XP. 

Question 2: If the answer to question 1 is Yes, then should the 60 gig be partitioned as ext3? 

Question 3: If the answer to question 1 is Yes, then what format should be chosen for the 40 gig partition used by XP and by Ubuntu? 

Although I've installed Hardy Heron three times, I've not before attempted an actual dual boot. I've been reading lots of posts in these forums but don't feel fully informed in regard to the above three questions. 

If the answer to q1 is No, then knowing that in advance would be helpful.

---

### Post by QIII on 2009-10-21
> My plan at this time is to allocate 60 gig to HP, 60 gig to Ubuntu, and (if possible) 40 gig to a partition for data files than can be read by XP and by Ubuntu.  Sounds doable.  Some may be of a different opinion, but you could keep the number of partitions to a minimum by just making one 100GB partition for XP -- a single NTFS partition.  Linux can deal with NTFS file systems and will be able to access whatever you save there.  Windows throws up, wets itself and generally has a bad day when it runs into an ext3 file system.  You can get Windows to work with ext3 if you want to jump through a lot of hoops.

> Question 1: Is the aforementioned 60, 60, 40 doable with the 40 read by both XP and Ubuntu?See above.  XP and Ubuntu are both comfortable with using files on NTFS partitions.

> I assume my first step will be to create three partitions in the 160 gig hd. The first partition will remain XP.Depending on how you want to partition, do that with the LiveCD.  Don't install Ubuntu with it just yet.  This goes a lot easier if you install XP first on the NTFS partition and install Ubuntu second.

> Question 2: If the answer to question 1 is Yes, then should the 60 gig be partitioned as ext3?Yes.  Or ext4.  I use ext4 on my Jaunty machines.  Edit -- On second thought: If you plan to use Hardy, it might be better to stick with ext3.  I can't say for sure how the kernel will deal with ext4.

> Question 3: If the answer to question 1 is Yes, then what format should be chosen for the 40 gig partition used by XP and by Ubuntu?As discussed above, Windows doesn't like anything but a Windows-centric file system.  However you want to partition, make the partition they share in common NTFS.

---

### Post by aspergerian on 2009-10-21
QIII, Thank you for the reply. Based upon what you said, I'll allow XP to remain installed on what MS calls drive C: (60 gig) and will probably create a data partition (40 gig), thus having 60 gig for Ubuntu. I'll probably install with 9.04. 

My plan (subject to correction and change) is first to create (based on your recommendations) the two NTFS partitions and also the third partition, which (I'm guessing) can be NTFS (at first, ie, prior to installing 9.04), after which the third (Ubuntu) partition will no longer be NFTS. 

I feel as if I ought create the three partitions at the beginning of this project. That way, when installing 9.04, I'll be able to choose intra-9.04 settings so that /home will have its own partition within the Linux partition of my hd.

This give me:
C: XP in NTFS partition
D: Data in NTFS partition
E: (not really) but this is where 9.04 will be. 

Question 4: If and and 9.04 is installing into partition "E", how ought I allocate the space within "E", which is (overall) the 60 gig I'm allocating to 9.04? (especially given my intention to have /home be separate from the 9.04 release)

---

### Post by QIII on 2009-10-21
Give this a read:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Instead of using FAT32 for the "data" partition, I'd go with NTFS.  It's a much better FS.

---

### Post by g160689 on 2009-10-21
20g(ntfs) for xp system programs only
30g(ntfs)for other software -xp
15g(ext3) ubuntu mount drive
10g(swap)
others for both xp and ubuntu-ntfs format will do.

---

### Post by QIII on 2009-10-21
10GB swap is over the top.

The max anyone recommends is 2xRAM, in this case that would be 4.  I think 2x is excessive.  1.5 might be better, or 3GB swap.  I usually go with 1.25x.

Also, you might consider Netbook Remix if your particular machine has the Atom processor.

---

