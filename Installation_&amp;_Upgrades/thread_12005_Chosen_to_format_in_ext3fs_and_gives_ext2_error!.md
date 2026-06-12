---
title: "Chosen to format in ext3fs and gives ext2 error!"
date: 2005-01-21
forum: Installation &amp; Upgrades
---

### Post by drbista on 2005-01-21
I have assigned various mountpoints to the different partitions and chosen ext3fs as my default fs. When I tried to finished the partitioning and assigning, then it gives an error that says:

!! Partition disks (red)
Not yet implemented (blue)
This ext2 filesystem has a rather strange layout! Parted can't resize this (yet). 
<Go Back>                                                                <Continue>

I have chosen everything in ext3fs. What could be the problem?


To make it much clearer, I am adding this:

When I select "Finished partitioning and make changes" with hda6 as /tmp by selecting the "keep the user data and use the partition", then it gives something like this:

The test of the file system with type ext3 in partition #6 of IDE1 master (hda) found uncorrected errors. 
If you do not go back to the patitioning menu and correct these errors, the partition will not be used at all.
Go back to the menu and correct errors?

When I say yes, then it shows the list again and I keep on running in the same cycle.

And I cannot format the partition because hda6 is also shared by FC1 as /tmp. ;-)

---

### Post by drbista on 2005-01-21
I read a similar problem at [http://ubuntuforums.org/showthread.php?t=983&highlight=parted+ext2](http://ubuntuforums.org/showthread.php?t=983&highlight=parted+ext2) but did not see any option like "Do not touch the partition" to make it through.

Is it a bug in ubuntu4amd64?

I could not proceed ahead for last more than one hour due to this problem and stuck at the Partition Disks stage? 

Are ubuntu deverlopers listening? Of course, IRC is of no use :-(( I experienced already.

---

### Post by dmatrix on 2005-01-21
Sounds like you partition layout is a little bit screwed up somehow.

Anyways try and not assign your other partitions on install. Only have one root '/' for Ubuntu and possibly use the same swap as you have for FC3. Do not assign any other partitions on install.

---

### Post by drbista on 2005-01-21
I do not agree with the screwy partitioning because it worked perfect with other distros. However, it seems like a bug to me that it has been mentioned in this thread:
[http://ubuntuforums.org/showthread.php?t=983](http://ubuntuforums.org/showthread.php?t=983)
and also here:
[http://ubuntuforums.org/showthread.php?t=9333&highlight=parted+ext2](http://ubuntuforums.org/showthread.php?t=9333&highlight=parted+ext2)

So it is not only my problem and my partition done with fdisk gone screwy. ;-)

And I do not want to go ahead without assigning separate partitions by compromising security vulunarabilities and crashes while compiling (I experienced these bitter truths earlier).

But I don't know exactly how could I insall in a single partition and then manaully assign different partitions different directories. ;-)

---

