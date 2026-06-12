---
title: "Help with disk partitioning on install"
date: 2008-11-01
forum: General Help
---

### Post by Universal344 on 2008-11-01
Hi, I am in the process of installing Kubuntu 8.10 with intention of dual booting it with my copy of Windows Vista Ultimate.  I reached the partitioning screen and clicked manual.  Now, I forget how to partition correctly.  I know I need one EXT3 partition and one Swap partition.  SO, I clicked free space and it brought up the dialog for a new partition.  I have the following questions:

Should i make the EXT3 primary or logical?

Should the location of the EXT3 be beginning or end?

What should the EXT3's mount point be?

The same questions apply for my Swap Partition.

Thanks for your help and I apologize for my ignorance.

---

### Post by uidb4056 on 2008-11-01
Regarding primary or logical depend on how many primary partitions you currently have, the maximum is 4 primary, if you need more you have to select logical.
I think EXT3 beginning is OK and Mount point has to be /
About swap you dont have to select Mount point.

---

### Post by Idefix82 on 2008-11-01
I recommend you to create
one ext3 partition with mount point / 
one ext3 partition with mount point /home
and one SWAP partition
in this order. If you only have one Windows partition, you can make all the partitions primary. For the swap partition you don't need to specify the mount point. How large they should be depends on how much space you want to allocate to Ubuntu. SWAP should be roughly the size of your RAM, / should be 10 GB or more, maybe up to 15 GB or even more if you have a lot of space and you can allocate the rest to /home. That's where you can put your data, like documents, music, pictures and that's also where your settings will be.

---

### Post by Universal344 on 2008-11-01
Thanks for the quick reply!  I have two Windows partitions though.  And I have a FAT32 partition for Acronis True Image (A piece of software that does a complete system backup and places it away in a hidden partition).  I don't know if its logical or primary.  Does this mean I should go with one EXT3 with a mount point of "/" and make it primary and one  Swap with no mount point and make it logical?  And can I get someone to confirm that beginning is correct for the EXT3 and what should the Swap be (Beginning or end)?

Thanks again!

---

### Post by Idefix82 on 2008-11-01
Some architectures require that the mount points of all the OSs should be among the first so-and-so many GB on the hard drive. That's why you should put the / partition first. On the other hand, speed is most critical with the SWAP partition and since the outer disks of the HD can be accessed faster than the inner discs (because the HD can rotate faster than the laser can scan along the radius) the SWAP partition should be the last partition on the HD.
You should make the / primary and the SWAP and /home (if you choose to create /home) logical.

---

### Post by uidb4056 on 2008-11-01
> **Universal344 said:**
> Thanks for the quick reply!  I have two Windows partitions though.  And I have a FAT32 partition for Acronis True Image (A piece of software that does a complete system backup and places it away in a hidden partition).  I don't know if its logical or primary.  Does this mean I should go with one EXT3 with a mount point of "/" and make it primary and one  Swap with no mount point and make it logical?  And can I get someone to confirm that beginning is correct for the EXT3 and what should the Swap be (Beginning or end)?

Thanks again!

According your info you will have already at least 3 primary partitions (you could check booting from LiveCD and execute Disk Partition from System-Administration menu), then you need to create the new partitions as Logical.

---

### Post by Universal344 on 2008-11-01
OK, I think I am going to go without the /home partition.  SO let me make sur I am clear on the rest.

EXT3:
Primary
35GB (I have 50GB free)
Beginning 
/

SWAP:
Logical
4GB (equivalent to my RAM)
End
(No Mount Point)

Again, I appreciate all your help!

---

### Post by uidb4056 on 2008-11-01
> **Universal344 said:**
> OK, I think I am going to go without the /home partition.  SO let me make sur I am clear on the rest.

EXT3:
Primary
35GB (I have 50GB free)
Beginning 
/

SWAP:
Logical
4GB (equivalent to my RAM)
End
(No Mount Point)

Again, I appreciate all your help!

If you create your EXT3 / as a primary and you already have before 3 primary partitions, you cant create SWAP as Logical, because the maximum primary partitions is 4 or 3 primary and one extended that you get creating Logical partitions. Inside the extended you can create as many logical as you want providing you have enough free space. When you create a logical partition a extended one is created automatically when you partition the install as manual.

---

