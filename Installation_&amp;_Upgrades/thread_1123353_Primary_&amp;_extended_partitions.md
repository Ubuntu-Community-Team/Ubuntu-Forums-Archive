---
title: "Primary &amp; extended partitions?"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by SupremeMoFo on 2009-04-12
OK, so I'm finally going to install Ubuntu. When I installed Vista on this laptop back in January, I gave Vista 50GB, Ubuntu 20GB (EXT3) and the remainder for programs/files.

Thing was, I didn't know about the swap partition. The problem is that there's a 78MB FAT16 partition before the Vista partition at the start of the drive, so that's all four primary partitions used up - FAT16, Vista, Ubuntu, and files. I need to put in a swap partition between the Ubuntu and files partitions (the space is there, I reduced the Ubuntu partition size to 16GB).

So, is the FAT16 partition there for a reason?

And I gather extended partitions can't be different file systems? (EXT3 and swap in my case)

Any help much appreciated!

---

### Post by Ticketoride on 2009-04-12
> **SupremeMoFo said:**
> The problem is that there's a 78MB FAT16 partition before the Vista partition at the start of the drive ... So, is the FAT16 partition there for a reason?

Check again ... it should be a 7.8 MB Partition.

An Extended Partition holding 1 or more Logical Drives. This is normal for MS File Systems.

If you make 2 Extended Partitions, you&#314;l have 2 of these 7.8 MB Jobs.

Don´t wipe it out if you have Logical Drives. It probably won´t let you anyways.

I suggest you clear some Space through Windows Software such as Partition Magic. Use Ubuntu&#347; GParted to resize as necessary. PQ Magic will also allow to make a Linux Swap Partition.

Its absolutely imperative you back up all Data on any Partition you will be modifying. GParted will convert any NTFS File System into FAT 32, but will wipe out all the Data in the same fell Swoop, something Win Partitioners won´t do.

---

### Post by Partyboi2 on 2009-04-12
You would need to delete one of your primary partitions before you could create the extended partition. Another solution could be to use a swap file instead of a /swap partition.

[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

---

### Post by SupremeMoFo on 2009-04-12
Oh... but I don't have any extended partitions currently? Depending on what Vista did when installing itself on the 50GB partition?

Cheers Party, I'll delete the EXT3 partition and try again, so gparted can do extended then?

---

### Post by ceylonerana on 2009-04-12
Are you sure that partition size is 78 MB or 7.8 MB. Because the least partition size should be 7.8 MB. Isn't it. How ever what is the total size of your HDD? 
I think anything wont happen when you delete the FAT16 partition. Also you had reduced your EXt3 to 16GB. So now you are having almost 4GB free space. Now you can select that free space to SWAP partition. You can do it when you create the partitions. Make sure to create a SWAP partition in this time.;) 
Have FUN with Ubuntu.:guitar:

---

### Post by Partyboi2 on 2009-04-12
> **SupremeMoFo said:**
> Oh... but I don't have any extended partitions currently? Depending on what Vista did when installing itself on the 50GB partition?

Cheers Party, I'll delete the EXT3 partition and try again, so gparted can do extended then?
Yes you can use gparted to create extended partitions.

---

### Post by SupremeMoFo on 2009-04-12
OK, extended partition created with EXT3 and logical partitions, there's 6.8MB unallocated either side of the extended partition though and I think this is what's causing me problems...

Also, that FAT16 partition *is* 78MB, not 7.8?

Now, trying to install from the live CD, it won't allow me to install without screwing around with the partitions - either wiping my entire drive or swapping the EXT3 and files NTFS partitions. How can I force it to install on the partition I tell it to? Do I need to download the installer ISO rather than the live ISO?

---

### Post by Partyboi2 on 2009-04-12
When you are at the partitioning stage of the install choose 'manual' and either create the partitions for ubuntu if you have not already done so or if you have already created the partitions before hand make sure that you set the mount point for the ext3 as / and that the swap is set as swap.

---

### Post by SupremeMoFo on 2009-04-12
Eep - OK, brilliant, so if you choose Manual, when you go "next" it THEN asks you where to install?

---

### Post by Partyboi2 on 2009-04-12
Yes, if you choose the manual option and press 'next' it will allow you to manually choose the partitions you want to install Ubuntu to. 
If you are not sure about the manual partitioning process have a look at 
[http://www.basicconfig.com/ubuntu_desktop_manual_partition_prepare_disk_space](http://www.basicconfig.com/ubuntu_desktop_manual_partition_prepare_disk_space)

It is a slightly different setup then yours but it will give you a general overview of the manual partitioning process.

---

