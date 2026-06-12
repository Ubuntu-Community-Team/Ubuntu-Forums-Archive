---
title: "How to reformat ubuntu startup usb drive?"
date: 2008-11-18
forum: General Help
---

### Post by KnavishClout on 2008-11-18
Hey everyone.  I installed ubuntu to a thumb drive to get some important files off of a friend's hard drive.  Now that the task is complete, I would like to go ahead and format the thumb drive back to fat32 or at least something Windows compatible.

The problem is that I don't know how.  GParted doesn't recognize it.  If I try to just delete the files (because it does mount under Ubuntu) it gives me an error about permissions. 

I'm very new to Linux and I prefer to use GUI whenever possible, so if you DO give me commands then please be as specific as possible because when it comes to Linux, I'm pretty much an idiot.

---

### Post by C.S.Cameron on 2008-11-18
In windows you can right click the flash drive and select Format.
Don't try this if it has multiple partitions as Windows can brick it.
If you are using gparted from the Live CD, go to System, Administration, Partition Editor.
Click the upper right corner and select the correct drive.
Right click the partition and Unmount, click again and Format to FAT32, click apply.
If there is more than one partition delete all and then create a new one.

---

### Post by KnavishClout on 2008-11-18
Thanks!  I can't believe I didn't notice that drop down box in the upper right corner.  I wouldn't have gotten it without your help, thank you!

---

