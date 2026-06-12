---
title: "4gb flash stick now 3gb!!"
date: 2008-08-24
forum: General Help
---

### Post by li10 on 2008-08-24
I was using the xubuntu liveCD and anfter trying to install to USB (silly me but I was bored) the memory stick now appears as 3gb instead of 4 as before. 

I deleted what was on the stick because booting from it didn't work, but there is a folder on there called "lost and found" which cannot be deleted (has a red cross on it). 

In Gparted there are two partitions on the disk - sda1 and unallocated. It's about 220mb so I want to get it back, how do I do this?

thanks, sorry for dipping in and out of the forums without helping anybody but expecting help, but I don't know much about linux at all.

---

### Post by kosmiciatakuja on 2008-08-24
Can you try to delete the partition in parted (or gparted or qparted) and then create a new one to fill the whole disk? 
Just be careful when deleting the partition - no to select the wrong disk :)
I know it's stupid but sh*t happens ;)

After creating the partition, remember to make a filesystem on it, like mkfs.ext3 /dev/sdX (replace X with the correct letter for your usb disk) or mkfs.vfat (if you want to read it in windows). 
You do the last step in 'sudo' if I remember correctly. Partitioning too I think. 

Be careful and triple check if you're doing this on the correct disk before deleting partitions and creating filesystems!!!

hope this helps.

---

### Post by aloshbennett on 2008-08-24
sudo rm -rf "lost and found" from command prompt should do it.

Remember to cd to the USB drive before you do that.

---

### Post by li10 on 2008-08-24
I can't delete any partitions on it, in terminal "fdisk /dev/sda1" tells me it is unable to open it. 

"sudo rm -rf "lost and found" doesn't do anything at all!! 

But thanks for replying, both of you.

---

### Post by aloshbennett on 2008-08-24
Is the drive mounted?

---

### Post by li10 on 2008-08-24
yeah I'll try unmounting it first now lol.

EDIT: just did exactly the same as before.

---

### Post by kosmiciatakuja on 2008-08-25
one more thing - try ```
fdisk /dev/sda
``` instead of ```
fdisk /dev/sda**1**
```!

---

