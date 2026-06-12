---
title: "Partitioning with CD"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by lhigg on 2009-10-31
Ok, I've finally gotten a CD, and I've been using Wubi, but I wanted the Speed advantages of ext3, so I decided to install, however, when I get to the partitioner, the only options it gives me are erase and use the entire disk, or set partitions manually, I have no idea how to do it manually, and when people keep saying things about "Size:" I don't see that anywhere. Can someone please help?

---

### Post by quixote on 2009-11-01
This is from memory, so I'll check more properly tomorrow and come back with any clarifications, but briefly the way it works is this:

Go for Manual partition. (I think it's step 5 of the install process?)

After you select that, there should be an option to set the size of the partition.  I'll look it up tomorrow and say exactly where to find it.

The system finds the largest block of free space and asks whether you want to use all of it for your ubuntu install.  If you want to leave some room to grow for your Windows partition, say no, and shrink down the size of the ubuntu partition-to-be by 5GB or whatever extra you want to leave for windows.

Choose the type of filesystem: ext3

After this there's only one essential job: next to "Mount Point" there's a dropdown menu.  Choose "/". 

"/" is the root directory and that says "put the operating system here." 

So, pretty simple:  [LIST]
[*]manual partition, 
[*]set size, 
[*]set ext3, 
[*]set root mount point,
[/LIST] 
and that's all.  (Actually, it's a good idea to make a separate /home partition.  If you want to do that, it's easy to do the three extra steps for that.  If you'd like the instructions, just say.)

Then a screen will come up asking you to confirm your choices and showing that it will reformat your new ubuntu partition.  Make sure your Windows partition is [COLOR="Red"]NOT[/COLOR] selected for reformat, and it won't touch it.  (It will say "ntfs" filesystem on the line.)

---

