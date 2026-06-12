---
title: "Need help on formatting two external HDD's"
date: 2010-12-24
forum: Hardware
---

### Post by subzero69 on 2010-12-24
Hey guys, i'm new to linux, got ubuntu 10.10. Converted from windows and loving it. Been learning linux for about 2 weeks.

Ok i'm having trouble trying to format two external HDD's. one is 160g and the other is a 1Tb.
I have googled this but still stuck.

I would like to format the 160 into two partitions of 80g's.
The 1tb is staying as a 1tb.

Both drives i would like to convert into FAT 32's. I have tried to partition the 160 into two 80's using gparted. But when i tested it on a windows pc (my freinds) the hard drive was not detected.

Cheers for the help and sorry to admins/mods if i have put my very first thread in the wrong location.

---

### Post by ajgreeny on 2010-12-24
> Both drives i would like to convert into FAT 32's. I have tried to  partition the 160 into two 80's using gparted. But when i tested it on a  windows pc (my freinds) the hard drive was not detected.

Have you actually tried gparted in Ubuntu yet?

If not run the live CD which has gparted available, or add gparted to your installed version of Ubuntu.

Then attach the USB drives, and when the icons appear on the desktop, right click on each and unmount them both.

Now run gparted from whichever system you have chosen to use, and the disks should appear as sdb and sdc, assuming you only have one internal hard disk.  Provided they both appear in the drop-down box at top right, you should now be able to delete the partitions already on them, and make new ones easily.  You may find that they are already fat32 and find that no action is needed, though the 160GB disk is likely to be a single partition, not two, of course.

---

