---
title: "replacing hard drive"
date: 2008-10-29
forum: General Help
---

### Post by metalmaniac248 on 2008-10-29
i will be getting a pc with a 250 gb hard drive, it will have intrepid ibex and windows vista installed,


 in the future should i wish to replace this drive with i larger one, is there any way i could copy the entire contents the 250 drive exactly to an external drive, then copy them back to the new larger drive, so i essentially have the exact same system but with more space.

---

### Post by TeXtonyx on 2008-10-29
Yes, it works this way. You connect the new drive as a slave which
means on the same cable as your current master. Change the jumper
settings; on the backs of the drive, they have a diagram of how to
place the jumpers. Your current drive should be jumpered as master
and the new drive jumpered as slave. Connect all the cables. After, 
you will probably reverse the settings for which is master and slave.

Then you clone the old drive to the new drive. The manufacturer of
the hard drive will have software to download which clones disks
among other things. Also Ubuntu probably has a program just for
cloning but many people use rsync. It may be a good idea to look up
installing a hard drive on Google, they have howtos with pictures.

---

### Post by Titan8990 on 2008-10-29
You could clone the drive but the problem is it will not increase the size of the partitions. What this means is that you will only be able to increase the partition size of the partition that is at the end of the disk.

I recommend using rsync. Basically you will make a rsync backup, install your operating systems and then restore the rsync. For Windows you can use Delta Copy (which is rsync).

To make the backup:

rsync -atvr / $DESTINATION

Then you will want to make sure to DELETE /etc/fstab from your backup. If you don't it will toast your new installation as /etc/fstab contains information specific your HDD.

After you have reinstalled Ubuntu:

rsync -vtr $BACKUPLOCATION $NEWINSTALLMOUNTDIR

You will want to do this from the live CD as it can cause problems trying to overwrite files that are in use.

I have tested this many times.

---

### Post by prshah on 2008-10-29
> **metalmaniac248 said:**
> 
 in the future should i wish to replace this drive with i larger one, is there any way i could copy the entire contents 

Sure, and it's really simple; only one command (and lots of time!) see [[SOLVED] Exact duplicate of entire HDD]("http://ubuntuforums.org/showthread.php?t=874643") for details. Post back if and when you need more help!

---

### Post by Titan8990 on 2008-10-29
Won't dd also copy the partition table and leaving him with the issue I described in my first post?

---

### Post by metalmaniac248 on 2008-10-29
> You could clone the drive but the problem is it will not increase the size of the partitions. What this means is that you will only be able to increase the partition size of the partition that is at the end of the disk.

I recommend using rsync. Basically you will make a rsync backup, install your operating systems and then restore the rsync. For Windows you can use Delta Copy (which is rsync).

To make the backup:

rsync -atvr / $DESTINATION

Then you will want to make sure to DELETE /etc/fstab from your backup. If you don't it will toast your new installation as /etc/fstab contains information specific your HDD.

After you have reinstalled Ubuntu:

rsync -vtr $BACKUPLOCATION $NEWINSTALLMOUNTDIR

You will want to do this from the live CD as it can cause problems trying to overwrite files that are in use.

I have tested this many times


the problem i have is that vista will be pre installed, so i won't havve a disk to reinstall it from, though i am hoping that by the time i have filled up the 250GB drive that i will have eliminated the need for any version of windows!!

---

### Post by linux_tech on 2008-10-29
Cloning software is the fastest way.  A 250GB drive will clone in about 20 min. I use ghost most often, but acronis is good also.  You just connect both drives, boot to the disk, then make sure you select the correct from and to, in 15-20 min its done.

---

### Post by prshah on 2008-10-29
> **prshah said:**
>  [[SOLVED] Exact duplicate of entire HDD]("http://ubuntuforums.org/showthread.php?t=874643") 

> **Titan8990 said:**
> Won't dd also copy the partition table and leaving him with the issue I described in my first post?

Yes, it will copy the partition table, and leave the rest of the hard disk unallocated; but the copied partitions can then be resized using gparted.

---

### Post by metalmaniac248 on 2008-10-31
if did the dd command and copied the drive to my external drive, how would i then copy that to the new internal drive?

---

### Post by shane19174 on 2008-10-31
> I use ghost most often, but acronis is good also.

Acronis is broken for partitions made with Intrepid (see [here]("http://ubuntuforums.org/showthread.php?t=964793") and [here]("http://ubuntuforums.org/showthread.php?t=899190")). Do you know if ghost still works?

---

