---
title: "Installing 9.04 to replace Vista without affecting other (non-OS) partitions"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by anuj016 on 2009-06-23
So I'm trying to install Ubuntu 9.04 to replace Vista on my Lenovo laptop. I have Vista installed on one 29GB partition and a second 105GB partition with tons of media files on it. Is there a way to install Ubuntu onto that first partition and replace Vista (i.e. no dualboot) without affecting the other partition? The partitions are both NTFS, by the way.

I tried by running the LiveCD boot and getting to the Partition Manager (Step 4 of 7) but the options I get are:

- Install Ubuntu/Vista side by side i.e. dual boot (which I do not want)
- Use the entire disk i.e. wipe out everything including the partition with my saved files (which I also don't want)
- Specify partitions manually 

I selected the third option but cannot figure it out. The partitions I see are:
- sda1 (~29GB, this has vista on it currently)
- sda5 (~105GB, this has my backup files)
- sda3 (~12GB, I have no idea what this is, unallocated space?) 

No matter what combination of partiton edits I choose, I get the following error message: "No root file system is defined. Please choose this from the partitioning menu."

Is there a way to get past here without wiping out my data on the second partition? It is backed up (mostly music, on my iPod) but I'd rather not have to spend the time re-importing it onto my laptop...

Any help for a newbie would be much appreciated!:)

---

### Post by Peder_Erickson on 2009-06-23
I'm assuming that you're using the manual partition editor, since you're getting the error.  Double click on sda1, choose a file system (EXT3 would be the best in my opinion), then type in '/' as the mount point (Remove the quotes), the format checkbox should be checked, then it should be able to go on.

You can set mountpoints for the other ones as well, if you want, or you can just mount them through nautilus when using Ubuntu.  Just make sure that the checkboxes aren't marked, if they are, all the data on those other partitions will be lost.

I hope that I told you what you need to know. :)

---

### Post by gallaharsha on 2009-06-23
As I see from your info:

sda1 which has vista installed need to be removed(assuming that you do not have any important files in the partition). So u can delete the partition and first create a root partition. The error your are receiving is because you do not have a root partition. Probably you can do this:

First delete the Vista partition(since you do not want to have it any more and I m assuming you want only one OS on your system i.e Ubuntu).

Then create a partition of the size of your choice(Minimum 10GB) of filesystem type ext3 and select '/' which means root partition.

Create another partition called swap space which can be about double the size of your memory(i.e if you have 1GB ram then make swap partition to be of 2 GB size) select type of partition to be Swap in the options list & files system to ext3 again.

Now you can click on the "\' root folder created in the second step and you will not get the error.

Hope this helps, Also if you are sure that the sda3 is not formatted it, you can create a partition of that in ntfs filesystem so that it could be used.

---

### Post by anuj016 on 2009-06-23
Thanks so much! I have it up and running, and love it. I used that whole unused portion for the swap, and the first partition as ext3. Thanks again!

---

### Post by gallaharsha on 2009-06-23
I dont think so much of swap will be of any use. usually 1GB of swap is more than enough

---

