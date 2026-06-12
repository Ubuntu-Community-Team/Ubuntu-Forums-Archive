---
title: "mdadm - Corrupted SATA Drive"
date: 2008-07-31
forum: General Help
---

### Post by OdorousSoup on 2008-07-31
I'm configuring a media storage machine with six hard drives - one of them is the boot partition, which will be backed up to the other five, which I intend to put in software RAID 5.

I'm using mdadm for this task, and I had it built fine with four of the drives.  When trying to add the fifth drive, however, I accidentally typed: ```
mdadm /dev/md0 --add /dev/sdd
``` I forgot the 1 at the end to indicate the correct partition.  When I tried to build the array, I checked /proc/mdstat and the time to completion started at 200 hours and kept climbing upwards.  At this point I stopped the array - but was unable to remove /dev/sdd because I could no longer assemble the array in order to do so.  After messing around with this for a while, I just decided to reinstall Ubuntu since I didn't feel like I was proficient enough in Linux to get everything fixed without completely resetting everything.

Unfortunately, after the reinstall, it seems that I can no longer access partitions on this /dev/sdd drive.  I can create them fine - the drive and partitions display and manage properly in fdisk and cfdisk.  However, after partitions are created I cannot access them - there is, for instance, no /dev/sdd1.  Similarly in blkid, the devices report as (I may be misremembering the type, but that doesn't seem like the important part):
```
/dev/sda1 type="ext3"
/dev/sda3 type="swap"
/dev/sdb1 type="fd_raid"
/dev/sdc1 type="fd_raid"
**/dev/sdd type="fd_raid"**
/dev/sde1 type="fd_raid"
/dev/sdf1 type="fd_raid"
```*Emphasis Mine*

As a Linux newbie, I just have no idea what to do at this point - any help would be greatly appreciated.

---

### Post by fjgaude on 2008-07-31
You grow an array by adding the new drive in as a spare then doing this:

```
sudo mdadm --grow /dev/md32 -n 4
```    # add a drive to 3-drive array

Well, I guess this typo has caused a drive to be in a sad state. You might try this command, being careful to get it right, no typos:

```
sudo dd if=/dev/zero of=/dev/sdd bs=1M count=1
```

Before doing this make sure of the drive name, the /sdd could have changed from the last boot.

With the **dd** command you have cleaned out the headers of the drive and it should be ready to be used again. Format it like the others.

There's lots to learn when using **mdadm**, so take a look at these:

Read, study: [http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
   then study **/usr/share/doc/mdadm/FAQ.gz**  and **md.txt.gz**

Let us know how you are doing.

---

### Post by OdorousSoup on 2008-08-01
Resetting the headers worked as far as getting the partition to be recognized - I rebuilt the array, and formatted it with ext3.  This all worked fine - I was able to mount it and copy files to it.

However, once I restarted the machine, the boot freezes for about two or three minutes just before the third tick mark on the progress bar.  The activity light on the drive which was having issues before is on continuously from this point forward.  After the machine finally boots, I can no longer see /dev/sdd1, although the partition is still visible via fdisk.  As a result, I cannot assemble my RAID device - I get the following message:
```
~$ sudo mdadm --assemble /dev/md0
mdadm: Failed to restore critical section for reshape, sorry.
```
Basically I'm back to square one on this - I could reset the headers on the drive again - but it doesn't seem like this is the issue?  I have attempted this three times (on fresh installations) - and I only have to create an array with /dev/sdd1 inside it in order to reproduce the issue (it occurs whether or not I allow the array to finish syncing).

---

