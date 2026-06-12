---
title: "Second hard drive mount point and file viewing"
date: 2008-04-12
forum: Hardware &amp; Laptops
---

### Post by countrylane on 2008-04-12
I have 2 hard drives. Ubuntu is installed on the first drive (HDA). I have a second drive (HDB) that has nothing but data files, spreadsheets, text documents etc... on it.

When I use the Gnome file browser (launched from PLACES>>>Home Folder), I am presented with my home folder stuff in the right pane and other locations in the left pane. One of those locations is 20.5GB MEDIA (my second hard drive).  When I click on the icon, a list of the files and directories for this drive  appears. So far so good.

If I then view the /mnt (on HDA), the file browser indicates it is empty.
If I view the /dev directory, I see /dev/disk/ and 3 sub-directories (by-ID, by Path, by UUID). All of the subdirectories have a handful of 0 byte files. The by-ID directory has what looks like references to my 2 hard drives, but you cant click on the links to see any files.

My drives appear to be in the /MEDIA directory....so I am assuming this is where they are mounted.

Right after I installed Ubuntu, my second hard drive appeared in the /MEDIA directory as DISK1, then DISK2, then DISK3, now DISK4.  DISK1, DISK2, and DISK3 are still there but are empty. All my second-hard-drive files appear under DISK4. I am going to assume that this will continue to happen and at some point I will have a DISK5, DISK6, etc.....

What is going on?

---

### Post by countrylane on 2008-04-13
Any help please?

---

