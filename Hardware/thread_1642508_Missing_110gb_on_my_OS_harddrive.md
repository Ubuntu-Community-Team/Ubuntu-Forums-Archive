---
title: "Missing 110gb on my OS harddrive"
date: 2010-12-10
forum: Hardware
---

### Post by CommuneOfLoon on 2010-12-10
I just built my first pc and installed 10.04 x64 on it. I'm utilizing a WD Black Cavier 750gb harddrive. When I go to File System, it says I only have free space of 640gb. I have yet to put anything on the drive other than the OS, and I'm wondering how I check what's going on, and more importantly how to fix it.

When I click properties for File System, it says the free space listed above, and then lists the content number as totalling 128TB! I have another installed internal harddrive (reformatted to ext4; 80gb) and two externals (125gb and 320gb), but I have no idea where 128TB comes from.

Just trying to give as much info as possible.

---

### Post by oldfred on 2010-12-10
Obviously 128TB is not correct. But properties has alway confused me. It does not count hidden files, but does count all the other mounts that I have. So it is part of one drive and parts of other drives.

What does this show, but it only shows mounted partitions.

df -H

Also hard drives count size as MB not MiB or GB not GiB.
[http://en.wikipedia.org/wiki/Gibibyte](http://en.wikipedia.org/wiki/Gibibyte)
[http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)

Formating a drive also uses about 5% for journal space.

---

### Post by CommuneOfLoon on 2010-12-10
> **oldfred said:**
> 
Formating a drive also uses about 5% for journal space.

0.05 of 750 is 37.5, plus the (I think) 10.5 for the root partition, and the OS can't be more than 5gb, leaving me with 697.5gb, not 640gb; almost 60gbs I'm missing.

BTW, what is this journal space?

---

### Post by oldfred on 2010-12-10
NTFS, ext3 and 3xt4 are journaled. That is they keep records of what is stored where and makes it more possible to recover data on file corruption.
[http://en.wikipedia.org/wiki/Journaling_file_system](http://en.wikipedia.org/wiki/Journaling_file_system)
Then when you format it, the ext4 is journalized so it reserves space for the journal. This improves performance and allows error correction for the cost of a small amount of space. Also reserves space.
[http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/](http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/)


You cannot start at 750 either, as that is only how hard drive mfgs. report it for sales. 
From link in previous post:
300 GB (279 GiB) hard disk is indicated only as 279 *GB*. As storage sizes increase and larger units are used, this difference becomes even more pronounced.

---

### Post by CommuneOfLoon on 2010-12-11
I was on another forum and somebody suggested utilizing sudo tune2fs -m [percentage] [path to device] to reclaim some of the journal space. They suggested for a drive as large as 750gb, only 2 or 3% journal space would be necessary. I just wanted to confirm that the command line and the reclamation of the 2 or 3% made sense. Thanks. 

    [FONT=Times New Roman][/FONT]

---

### Post by oldfred on 2010-12-11
I would not do that on the system partition, but I think it would be ok on any data partitions. Are you that tight for space?

I like to keep system partitions relatively small, all mine are 20-25GB but I keep all data in other partitions. Small systems partitions slightly improve performance as the files are closer together on drive. My system partiton usage is about 6GB, but if you write to a DVD you may need the 4GB in /tmp just for a while. I also found another reason to have it a little larger. I though I was writing my backups to my backup partition, but my latest install does not have that mounted, so it is writing into /, I would have been in real trouble if I did not have some working room.

---

### Post by CommuneOfLoon on 2010-12-12
I have heard to separate the disk into an OS and data partition; I probably should have done that. Well, at least I know for next time. Thanks for the info, Oldfred.

---

### Post by pseudo endeavor on 2011-01-17
I've run "sudo tune2fs -m 0 /de..." on my /home partition. I received the "Setting reserved blocks percentage to 0% (0 blocks)" confirmation. However the partition remains unaffected. I've tried rebooting. I've even tried a fresh install and reformatting the partition with 0% reserved blocks manually. My system monitor still shows /dev/sda3 /home 282.1GB. I should have 308.

---

### Post by oldfred on 2011-01-18
Everyone counts differently. If you look at gparted, df -H, & system monitor you get different results. 

If you are that close to filling drive it is time for a new drive anyway.

---

