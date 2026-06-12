---
title: "Reclaim some NTFS space"
date: 2006-05-22
forum: Hardware &amp; Laptops
---

### Post by GoodPanos on 2006-05-22
I know before installing a Linux distro you can repartition free space of NTFS into Linux file system.

How about when you already have installed Linux, in this case Ubuntu and you want to add more space to it?

For instance I want to take away 10GB from my Windows XP NTFS partition and add it to Ubuntu.  Is this possible?  If so, any steps whould be greatly appreciated.

Never knew that I was going to be using Ubuntu a lot more than XP ;)

---

### Post by olsonar on 2006-05-22
easy. just

```
sudo apt-get install gparted ntfsprogs
``` 
then go to System -> Administration -> Gnome Partition Editor

---

### Post by aysiu on 2006-05-22
I don't think you can add space to the beginning of a partition, only to the end of it. So if Windows is before (to the left of) Ubuntu on the your drive, you won't be able to tack on freed-up NTFS space to the Ubuntu installation unless it's as a separate data partition.

---

### Post by GoodPanos on 2006-05-23
> I don't think you can add space to the beginning of a partition, only to the end of it.
I'm not sure I follow. :neutral: 

The way my system is setup is as follows.
Partition 1: WinXP 20GB (this is where the OS is located)
Partition 2: Boot loader
Partition 3: Ubuntu 18.7GB
Partition 4: NTFS 35.5GB (This is the partition I want to take away 10GB and add to the above.  I just store data here)
Partition 5: Swamp

---

### Post by aysiu on 2006-05-23
[QUOTE=GoodPanos]I'm not sure I follow. :neutral: 

The way my system is setup is as follows.
Partition 1: WinXP 20GB (this is where the OS is located)
Partition 2: Boot loader
Partition 3: Ubuntu 18.7GB
Partition 4: NTFS 35.5GB (This is the partition I want to take away 10GB and add to the above.  I just store data here)
Partition 5: Swamp[/QUOTE] If you delete Partition 4, you can resize Partition 3 to include that newly created space. 

However, you cannot resize partition 4 and somehow add the newly created space to Partition 3, since Partition 4 is in the way. 

Resizing happens from right-to-left. You can't take space out of the beginning of Partition 4 and add it to the end of Partition 3.

---

### Post by GoodPanos on 2006-05-23
Got it.  :eek: 
I'm just going to have to move some files around and delete partition 4.

---

### Post by GoodPanos on 2006-05-30
Just thought of something else.

Since Dapper is coming out pretty soon I was thinking what if I delete both Linux partitions (3 & 5).  Could I then take away 10GB from the 2nd NTFS (4) partition?

---

### Post by aysiu on 2006-05-30
[QUOTE=GoodPanos]Just thought of something else.

Since Dapper is coming out pretty soon I was thinking what if I delete both Linux partitions (3 & 5).  Could I then take away 10GB from the 2nd NTFS (4) partition?[/QUOTE] I think you'd still have the same problem--that the NTFS partition is jammed between 3 & 5. 3 & 5 would now be empty spaces, but you wouldn't be able to add anything to 3.

---

### Post by GoodPanos on 2006-05-30
Once I delete 3 & 5 doesn't that go at the end as unpartitioned space?  And then couldn't I take away 10GB from the NTFS partition and add it to the unpartitioned?

---

### Post by aysiu on 2006-05-30
[QUOTE=GoodPanos]Once I delete 3 & 5 doesn't that go at the end as unpartitioned space?  And then couldn't I take away 10GB from the NTFS partition and add it to the unpartitioned?[/QUOTE] I'm about 90% sure of this based on my experiences, but someone more knowledgeable can correct me on this if I'm wrong...

When you delete the space, it's still in the same spot, but I think the number goes up.

For example, if I have /dev/hda5 and /dev/hda6 and resize /dev/hda5 and free up some space, the space is still between /dev/hda5 and /dev/hda6, but it gets numbered /dev/hda7.

---

