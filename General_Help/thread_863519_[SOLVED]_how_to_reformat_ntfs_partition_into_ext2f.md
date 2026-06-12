---
title: "[SOLVED] how to reformat ntfs partition into ext2fs?"
date: 2008-07-18
forum: General Help
---

### Post by kernelhaxor on 2008-07-18
I have a dual boot Ubuntu and Vista ..
Now I want to completely wipe off vista :guitar: .. so how do I reformat that drive and change the filesystem to ext2fs from ntfs?

Thanks

---

### Post by Potatoj316 on 2008-07-18
Usually Ubuntu uses the ext3 fs but either way the instructions are the same.  Boot into the live CD environement and use the Gnome partition editor (under the administration menu) Then delete the ntfs partition and resize the Ubuntu (ext2/3) to use up the extra space

---

### Post by jimv on 2008-07-18
Or just install Gparted in Ubuntu and don't worry about the live CD:

sudo apt-get install gparted

Then you'll have the Partition Editor in System > Administration.  Just right click on the NTFS partition and click Unmount (if it's mounted) an then right click it again and click FOrmat To > Ext3

---

### Post by Potatoj316 on 2008-07-18
You can do that but you will not be able to put the 2 partitions into 1, it will be like having 2 hard drives, you will have to specifically mount the second partition to use it, and files will not go there by default.  The reason for this is gnome partition manager can not work on partitions that are in use, and that partition has to be in use to run gnome partition editor

---

### Post by kernelhaxor on 2008-07-18
Thanks guys! I figured it out.

---

### Post by jimv on 2008-07-18
> **Potatoj316 said:**
> You can do that but you will not be able to put the 2 partitions into 1, it will be like having 2 hard drives, you will have to specifically mount the second partition to use it, and files will not go there by default.  The reason for this is gnome partition manager can not work on partitions that are in use, and that partition has to be in use to run gnome partition editor

Yeah, I figured he wanted to use the Vista drive as a storage drive.

---

### Post by bodhi.zazen on 2008-07-18
Woot ... :guitar:

Please mark this thread as solved, it saves the time of many volunteers looking to help 
[indent]... and users looking for solutions.[/indent]

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by kernelhaxor on 2008-07-18
> **bodhi.zazen said:**
> Woot ... :guitar:

Please mark this thread as solved, it saves the time of many volunteers looking to help 
[indent]... and users looking for solutions.[/indent]

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Done.  Will keep tht in mind ..

---

