---
title: "Partition editor"
date: 2008-07-27
forum: General Help
---

### Post by vze57gc8 on 2008-07-27
so i have ubuntu installed on my laptop and i want tona do a dual boot with ubuntu and backtrack3.i installed partition editor to allocate space for bk3 but when unmounting the main partition (/dev/sda1) file system ext3 i get a messege saying... 

"Could not unmount /dev/sda1. The partition could not be unmounted from the following mountpoints:

/

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually."

Now im stuck and have no idea what to do. Can some1 plz coach me through?

---

### Post by ajgreeny on 2008-07-27
Firstly, backup, backup, backup.  Now if things should go wrong (no real reason they should, but - - -) you will be able to restore your important files.

OK, now we're ready to start.  Fire up the ubuntu liveCD and go to *Gnome Partition Editor*.  I can't remember exactly where in the live CD menu it appears, but it is definitely there somewhere.  That will allow you to work on the partitions on your hard disk without problem.

You can not use your installed ubuntu on the hard disk, to work on its own partition, because in order to run it must obviously be mounted, and gparted can not do anything to a mounted partition.  The live CD does not mount partitions by default, so no problem running that.

---

