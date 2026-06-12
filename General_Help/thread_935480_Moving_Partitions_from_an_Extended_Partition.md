---
title: "Moving Partitions from an Extended Partition"
date: 2008-10-01
forum: General Help
---

### Post by acer34e on 2008-10-01
I installed Ubuntu 8.04 onto a Dell Machine that had XP installed and it had a hidden partition. Once I copied all of my data from the XP partition, I planned to delete the partition and resize the Ubuntu partition with Gnome Partition Editor. It turns out that the Ubuntu partitions were created in an extended partition and I can't resize it. I very passively tried to back up the partitions to another hard drive using Clonezilla intending to then delete the Source partitions and copy back over in a clean fashion, but the destination backup was not recognizable afterwards.
Does anyone have an idea for how I can do this without having to reinstall? The partition table is too sloppy for my tastes (I have an HDA2, HDA5 and HDA7 kicking around there).
Thank you!

---

### Post by plucky on 2008-10-02
> It turns out that the Ubuntu partitions were created in an extended partition and I can't resize it.

You need to use the Live Cd to resize partitions and it won't allow you to resize it if there is a mounted partition within the extended partition.

When you run the partition editor from the Live cd,if the partitions are locked,it will show a key icon.Also the Live CD will use the swap partition,so you have to turn swap off.

Just select the swap partition,right click and select swapoff.

Resizing the partitions won't change their designations so after the resize you will still have hda2 as your extended partition.


Good Luck

---

### Post by vanadium on 2008-10-02
As soon as there is a need to move the partition, consider a reinstall: that will be much faster than moving a partition. Resizing partitions is a fast proces, moving partitions is a very lengthy process.

---

### Post by GetVerticalPV on 2008-10-04
acer34e, 

I am in the same situation - I installed Ubuntu on my Dell desktop to try it out and at this point I haven't used Vista for over 3 months and want to reclaim the space.  How did you resolve this?

---

### Post by bodhi.zazen on 2008-10-04
There are several issues here. First the "hidden" partition is typically your restore partition. Before you delete it, be sure you have made a restore CD if you so desire.

Second, you can only have 4 primary partitions. See :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

Next you should manage your with a live CD.

And last, with extended partitions you need to do the operation in two steps. First resize the extended partition, then apply changes, then resize the logical partition.

    Documentation: [Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by acer34e on 2008-10-04
Thank you everyone for the information!
GetVerticalPV: I haven't come to a decision yet as I am considering the advice from vanadium. I am most likely going to wait until Intrepid Ibex is released, back everything up and do a fresh install.
Unfortunately a Gparted LiveCD doesn't have the correct video settings (VESA included) so I have to boot in using Knoppix. I still haven't been able to resize the Extended Partition.
bodhi.zazen is right and you should make a restore CD as the hidden partition holds all of your Windows Drivers and more. I just created a FAT32 partition at the end of the hard drive with the Dell Drivers just in case, but this computer has been claimed by Ubuntu.
I will still play around with trying to resize the extended partition in the meantime. The big problem is I ran out of space. I had to create a separate ext2 partition so I could seed Intrepid Ibex beta cd (we all do our part). I will upload a gparted screenshot on Monday illustrating my problem, but for the most part I think I will wait until the end of October. Cheers!

---

