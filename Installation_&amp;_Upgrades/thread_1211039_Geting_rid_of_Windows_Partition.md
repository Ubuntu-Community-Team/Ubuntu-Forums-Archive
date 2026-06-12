---
title: "Geting rid of Windows Partition"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by shadysamir on 2009-07-12
I have a dual boot machine with Windows XP and Ubuntu Jaunty on the same hard drive with 2 partitions (ntfs and ext4). I've used them side by side for a while but now I want to sack windows completely and keep only ubuntu. How can I do that without losing any data from my ubuntu installation?

The boot loader is on the ntfs partition which is the primary one. The ext4 is extended.

---

### Post by ajgreeny on 2009-07-12
You can just use Partition-Editor (gparted in synaptic) to delete the windows partition, but you will have to use the live CD to move your ubuntu partition to the start of the drive into the free space, so you might as well do everything with the live CD.

Boot ubuntu liveCD, go to System > Administration > Partition Editor. In that you will see your partitions in a diagramatic style.  Right click on the first one which will probably show as NTFS, and choose delete.  This action will be added to a list of actions pending at the bottom.  If the delete option is greyed out, it may be because the partition is mounted so choose unmount first, then delete.  Now choose the extended partition that contains the ubuntu partition and click on the Resize/Move button, and drag the left end of the partition to the furthest left.  That action will also be added to the pending list. Now do the same to the ubuntu partition itself.  Now check this is what you want and click Apply.  It will take a long time to move the partition back on the disk, but don't worry, it should go without problem if my experience is anything to go by.

Don't worry about loosing grub; you probably won't, because it is not actually on the windows partition normally, just the first section of the disk itself, but even if you do, you can get it back very quickly with this [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by shadysamir on 2009-07-12
Thanks for your reply.

I just resized my windows partition using live cd but I cant move my ubuntu partition to the left into the free space. If I totally remove the NTFS partitions will I be able to use this space?

I guess there is an issue of Windows being a primary partition and ubuntu is extended? I ended up moving swap into this new free space and growing the ubuntu partitioon into the new free space in the end (extra 2.5GB) where swap used to be.

I had to install grub again after the resize so I've been through the process already. So I guess I will just repeat the same steps if I remove the Windows partitions.

---

### Post by ajgreeny on 2009-07-12
You said your ubuntu is in an extended partition, so you need to enlarge the carrier partition first then the ubuntu partition.  If you're not sure about this, add a screenshot of gparted to a postor the output of sudo fdisk -l and I'll help you again.

It will probably show partitions sda1 (windows), sda2 (the extended partition) and sda5 (the ubuntu logical partition inside sda2) and maybe sda3 or sda6 swap.  Let's see and we'll go further.

---

### Post by shadysamir on 2009-07-12
Here is a screenshot attached.

/dev/sda1 is windows system partition
/dev/sda2 is a partition with my documents folder from windows, I am using it as well from ubuntu but will probably just back up all files and move everything in it to my home folder under ubuntu

---

### Post by ajgreeny on 2009-07-12
If you are really going to get rid of the sda2 and do a backup and clean start, then the simplest way is to use ubuntu live cd and delete all partitions on the disk, (after backing up, of course), or just use the install button on the live CD and choose to use the whole disk.  The install will set everything up for you including swap, and you will need to do little else, except choose username and location, etc.  I honestly think this will be the quickest, particularly if you have not installed a lot of extra applications over and above the default ubuntu set.

If you want to keep the current install, because you have added lots to it and want to keep the setup, etc,, as I said, boot to the live CD and from there you can delete your windows partition(s).  If you choose to keep the sda2, which has the data on it, you will have to move that to the front of the drive, in place of the sda1.  It will, however, leave you with an NTFS partition which is not so useful without windows to defrag it etc etc.

Now right click on the swap and unmount it and then either delete it or move that also to be beside sda2, but don't enlarge it.  There should now be some free space between the swap and your ubuntu partitions, so click on the sda3, the extended partition, and enlarge that to fill the space by moving its left margin fully to the left.  Now do the same with sda5, your real ubuntu partition.  Finally click apply, and hopefully all these pending actions will occur without any problems.

Good luck, I hope it all works OK for you.  I have done similar things, just shrinking my windows partition myself, in the past, and apart from the long time it takes, everything went without a fault.

---

### Post by raymondh on 2009-07-12
[https://help.ubuntu.com/community/HowtoPartition/MovingPartition](https://help.ubuntu.com/community/HowtoPartition/MovingPartition)
[https://help.ubuntu.com/community/HowtoPartition/ResizingPartition](https://help.ubuntu.com/community/HowtoPartition/ResizingPartition)
[http://gparted.sourceforge.net/larry/livecd/livecd.htm](http://gparted.sourceforge.net/larry/livecd/livecd.htm)

---

