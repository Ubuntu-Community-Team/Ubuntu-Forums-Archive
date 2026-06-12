---
title: "Partition Help"
date: 2008-08-28
forum: General Help
---

### Post by intense.ego on 2008-08-28
I have a 60gb hard drive and on it I have the following partitions:

windows - 6 gb
ubuntu / - 10 gb
ubuntu /home - 40gb
extended -> swap - 1 gb

(not exaclty 60gb because of bytes/bits issues)

Now, here is my problem. I want to insall arch linux but plan on creating the partitions first, so I booted into an ubuntu liveCD and opened up gparted. I freed up some place but then I found out that an HDD can only have four logical partitions. The solution, apparently, is to create extended partitions and logical partitions within that.

The solution I have come up with is this:
extended 1 -> windows + data (to be created)
extended 2 -> ubuntu / and /home
extended 3 -> arch /
extended 4 -> swap

(NOTE: arch will be sharing the home partition with ubuntu - same partition different directories)
(NOTE 2: arch will be in an extended partition even though it doesn't have to be, so that in can be used in the future for more partitions)

So, how do I get my old set up to turn into my new setup (using Gparted)? Remember I cannot create any new partitions because I have used all 4 available ones. Is there a way to transform or change partitions? (i.e. logical into extended)

EDIT:

whoops! I just realised that there can only be one extended, so what do I do? Should I just create all the arch directories in the existing extended partition? But if the "unallocated space" is in the HDD and not the extended partition, how do I do this?

---

### Post by Taxman415a on 2008-08-28
I can't remember all the terminology, but there can only be 4 primary partitions, but inside an extended partition there can be quite a large number of logical partitions. Windows doesn't do well booting with them so leave it in it's primary partition and yeah, just create logical partitions for your arch linux. Grub should be able to figure out how to boot from that just fine.

---

### Post by intense.ego on 2008-08-28
I understand that, but how do I change a partition from logical into extended? And then how do I move partitions from underneath the HDD to underneath the extended partition?

---

### Post by Taxman415a on 2008-08-28
You mean change it from primary to extended? Just use gparted and change the partition type. Luckily you can do that with your swap partition without having to back it up and redo it since it's swap. Or just delete the swap partition and create a new extended partition with the free space. But if your swap is already in the extended partition, just create more partitions in the extended partition. As for moving partitions, you can do that if you have extra space to store the backup images, but why would you need to? You already have three primary partitions and can make or have an extended one and can make new partitions under that extended one so you should be fine. I've never done it, but this tool looks like it can handle backing up and restoring partition images [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

### Post by intense.ego on 2008-08-28
Exactly how do I change the partition from logical to extended?

Also, how would I move a logical partition so that it becomes a part of an existing extended partition?

Here is a screenshot of what gparted looks like now (attached)

---

### Post by intense.ego on 2008-08-28
Actually, nevermind my previous post, I think I have found out what to do (correct me if I'm wrong):

1) Delete the extended partition
2) Create new extended partition with all the unallocated space
3) create a new swap within the extended partition
4) create arch linux root within the extended partition
5) create data partition within the extended partition

So it would be:

A) windows
B) Ubuntu /
C) Ubuntu /home (and future arch /home)
D) extended, with
       swap
       arch root
       data

However, I have a question. Since I will be deleting and making a new swap, will Ubuntu know what to use?

---

### Post by plucky on 2008-08-28
Why delete the extended partition? Just follow this sequence using the Live CD.

1) Shrink /dev/sda4 just enough for your Arch partition.This will leave some unallocated space.
2) resize your extended partition to take up the unallocated space
3) Create a logical partition inside the extended partition, using the unallocated space, for Arch.
4) Leave the swap partition as is.


> Since I will be deleting and making a new swap, will Ubuntu know what to use? 

If you make a new swap,the UUID will change and you would have to edit your /etc/fstab file to reflect the new UUID of the swap partition.


Good Luck

---

### Post by rdpsycho on 2008-08-28
insert your windows 95 startup disk and type fdisk you will find the option in there

---

### Post by intense.ego on 2008-08-28
> **plucky said:**
> Why delete the extended partition? Just follow this sequence using the Live CD.

1) Shrink /dev/sda4 just enough for your Arch partition.This will leave some unallocated space.
2) resize your extended partition to take up the unallocated space
3) Create a logical partition inside the extended partition, using the unallocated space, for Arch.
4) Leave the swap partition as is.




If you make a new swap,the UUID will change and you would have to edit your /etc/fstab file to reflect the new UUID of the swap partition.


Good Luck

Okay, thank you. I will do what you said and report back to tell you if it is successful.

---

### Post by Taxman415a on 2008-08-28
Yep, now that you've posted that screenshot it's clear you already have an extended partition, so plucky's steps should work fine. If you do delete and recreate the swap you'll also want to fix the UUID in /etc/initramfs-tools/conf.d/resume so your suspend and resume still works, following coffeecat's post in this thread: [http://ubuntuforums.org/showthread.php?t=857565](http://ubuntuforums.org/showthread.php?t=857565)

---

