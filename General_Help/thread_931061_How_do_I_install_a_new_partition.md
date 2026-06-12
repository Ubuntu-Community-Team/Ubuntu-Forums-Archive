---
title: "How do I install a new partition?"
date: 2008-09-26
forum: General Help
---

### Post by shafin on 2008-09-26
Hi,
I recently upgraded my HDD and copied the partitions from the old one using a disk duplicator. As I have a dual boot system, I decided to keep the partition structure intact. However, I planned to migrate my home folder to a separate partition, so I left about 30 GB space for that. Everything wnet smoothly for ubuntu :). I am able to boot from the new HDD, though thats not the case on windows, but thats another story.

Now let me come to my problem. When I created an ext3 partition in this unallocated space using GpartED, the new partition, for some strange reason, gets tagged as a 32 Gb removable drive in nautilus. What is more, It's there but I can not mount it. I tried adding the UUID to fstab to no avail. Then I ran nautilus as root, and found that the partition is not available there, even as an unmounted one. Please guide me on how I can mount this partition.

Thanks in advance.

---

### Post by JC Cheloven on 2008-09-26
You're probably aware of that, but just in case: how many partitions do you have? all of them are primary, or some on them are logical, inside an extended one? 

I'm thinking about that limit of 4 primary partitions per disk. Anyway, could you post the output of  "sudo fdisk -l"  ?

---

### Post by bigbrovar on 2008-09-26
try follow this guide i gave a while back [http://ubuntuforums.org/showpost.php?p=5045657&postcount=5](http://ubuntuforums.org/showpost.php?p=5045657&postcount=5) 
 then to set the right permission [http://ubuntuforums.org/showpost.php?p=5046302&postcount=14](http://ubuntuforums.org/showpost.php?p=5046302&postcount=14)

---

### Post by shafin on 2008-09-26
```

$sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x349ed9fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4220    33897118+   7  HPFS/NTFS
/dev/sda2            4221       26544   179317530    5  Extended
/dev/sda5            4221        9442    41945683+   7  HPFS/NTFS
/dev/sda6            9443       12706    26218048+   7  HPFS/NTFS
/dev/sda7           12707       12993     2305296   82  Linux swap / Solaris
/dev/sda8           12994       14142     9229311   83  Linux
/dev/sda9           18059       21322    26218048+   7  HPFS/NTFS
/dev/sda10          21323       26544    41945683+   7  HPFS/NTFS
/dev/sda11          14143       18058    31455238+  83  Linux

Partition table entries are not in disk order


```

And here is the physical position of my partitions, sda11 is the partition in question.

[IMG]http://img205.imageshack.us/img205/4898/screenshot1mb1.png[/IMG]

---

### Post by shafin on 2008-09-26
@[bigbrovar]("http://ubuntuforums.org/member.php?u=322158"):Thanks for the link. It worked :)

Now on to migrating my home partition.

---

### Post by shafin on 2008-09-26
I'm still having one problem, the drive is mounted as a removable drive. How can I mount it as a HDD partition?

---

### Post by bigbrovar on 2008-09-26
does it automatically mounts when u reboots? what do u mean by "the drive is mounted as a removable drive"

---

### Post by shafin on 2008-09-26
It mounts automatically, what I mean is, the drive is mounted the same way a removable drive would be mounted. It is shown on the places menu under removable drives.

---

### Post by bigbrovar on 2008-09-27
I dont know about that .. afaik when u mount an external drive there is alway an option to umount it when u right click on the drive icon .but that shouldnt be a major problem as far as it works fine

---

### Post by shafin on 2008-09-27
Well, I'm on Intrepid,and there are icons to unmount every partition in the sidebar.

BTW, the problem is irrelevant now. I transferred my Home folder to the new partition and now the partition is working fine.

Thanks a lot for helping :)

---

