---
title: "Ubuntu partitioning problem"
date: 2008-08-21
forum: General Help
---

### Post by drshahab on 2008-08-21
Hi all,
I'm facing some problems with the partitioning tool when I was trying to install Ubuntu. But before I go on about that, just like to give you a little insight into this 250 gig HD's complete history..

When I first brought this HD, I wanted it to retain the data that was kept in my previous 40 gig HD. I used Acronis True Image 8 to clone the disk and its 5 partitions, the new partitions were made in the ratio of the previous one, hence, they covered the whole HD.

Then I used the gparted (GUI version) boot disk to resize my partitions. I shortened the size of all existing partitions according to my liking, and then I created a 6th 125 gig NTFS in the remaining space for storage purposes. At that point, I also left 11.5 gig of completely free space because I had the intention of installing Linux. Now then, all the previous partitions which I had cloned were FAT32, I converted them to NTFS using XP's built-in tool.

Everything went fine and dandy apart from the fact that 2 of the 3 XP's I had became un-bootable due to the hall.dll issue (mentioned in another thread). After installing fresh XP's in those partitions, I got down to filling up the massive new space I had at my disposal (its what I do best)

Right then, onto present day. I started the Ubuntu installation, I had the intention of creating one 5 gig partition for installation files, another 5 gig home partition (with a /home mounting point) for personal files and the left-over 1.5 gig for swap area.

The problem is that when I create anyone of these partitions (I use the manual option), the rest of the space becomes "unusable". Can anyone help me out please, I really like Ubuntu when I use the live CD and I would love to use it (in dual-boot with 2 XP's that is)

Note: To stop my first post from being too complicated, I have neglected to mention whether the partitions are primary, logical or extended, but please ask me to do so if it is required.

Edit: Here's a screenie from the gparted gnome partitioning tool

---

### Post by lackoblacko on 2008-08-21
there is a limit of 4 for primary partitions on a hard drive.

read here on how to create more than 4 partitions.

[http://www.bleepingcomputer.com/tutorials/tutorial115.html](http://www.bleepingcomputer.com/tutorials/tutorial115.html)

---

### Post by BarryMaccaukner on 2008-08-21
Yeah, you can only have 4 primary partitions , but you are only limited to the letters in the alphabet to make logical partitions

---

