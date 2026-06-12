---
title: "dual boot partition advice"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by Mash909 on 2009-11-07
Hi

I'd like to install Ubuntu on my existing Windows XP box, dual-booting with the existing XP installation.

Ubuntu installation reports that there are already several partitions present:

```

/dev/sda
  /dev/sda1     Dell utility partition         Fat16   57mb
  /dev/sda2     WinXP                          NTFS    234424mb
  /dev/sda4                                    FAT32   3399mb
  /dev/sda5                                    NTFS    79999mb
  free space                                           8mb

```In XP win explorer I have a C: and D: drive - which are not separate disks, but partitions.

I'd like to install Ubuntu into the D: partition, which I guess is /dev/sda5 (NTFS) in the partition table above.

How should I achieve this during Ubuntu installation (format /dev/sda5 as ext3?)
Where do I set the mount point, and how will the bootloader know to boot into this partition for Ubuntu?

I have no idea what the other smaller partitions on the disk are for!

---

### Post by Megaptera on 2009-11-07
I left the smallest Dell one well alone on my Dell laptop. I think you're right about your 'D' but other than that - sorry. But my Dell with Vista  dual boots fine with Linux (if that's any re-assurance?!)

---

### Post by conrados1 on 2009-11-07
Well what I have done is take the D partion cut it to 3GB and use the 4.9GB for Ubuntu. But that is after you run system defragment or what ever its called to group the files to make sure nothing is messed up.):P

---

### Post by Shazaam on 2009-11-07
Do us a favor and post the output from this (use the Ubuntu livecd)...
```
sudo fdisk -lu
```
(lowercase L)
Looks like you have plenty of room by your first post. Defrag XP first then resize/shrink a partition (sda5?) using the Ubuntu livecd. Stay away from/leave the small partitions. When done boot back into Windows and run a chkdsk. From there reboot to the Ubuntu livecd and you can install it. I highly recommend bypassing the "Guided" partitioning scheme and choose "Manual" during installation. That way you reduce the chances of accidently overwriting XP.

What has worked for me...
1. Defraged XP.
2. Rebooted to the Ubuntu livecd.
3. Used Partition Editor (gparted) and shrank the XP partition.
4. Created an Extended partition in the new unallocated space.
5. Rebooted to XP- ran chkdsk.
6. Rebooted the Ubuntu livecd and installed Ubuntu inside of the Extended partition using the "Manual" method.

---

### Post by Mash909 on 2009-11-09
Thanks for the responses.

My fdisk output is:

```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      112454       56196   de  Dell Utility
/dev/sda2   *      112455   462270374   231078960    7  HPFS/NTFS
/dev/sda3       462286440   618534629    78124095    f  W95 Ext'd (LBA)
/dev/sda4       618534630   625137344     3301357+  db  CP/M / CTOS / ...
/dev/sda5       462286503   618534629    78124063+   7  HPFS/NTFS

```I've also added the GParted image at:

[IMG]http://www.imagechicken.com/viewpic.php?p=1257771998096692500&x=png[/IMG][IMG]http://www.imagechicken.com/viewpic.php?p=1257771998096692500&x=png[/IMG]http://www.imagechicken.com/viewpic.php?p=1257771998096692500&x=png

What's confusing me is why is /dev/sda5 nested under /dev/sda3?

I guess that the /dev/sda5 partition is large enough that it doesn't need resizing for Ubuntu, so I might be ok there.  But what exactly do I need to do with GParted in order to get a partition suitable for Ubuntu installation?

thanks
Matt

---

### Post by qwerty57 on 2009-11-09
Windows actually takes up two partitions, one for XP or Vista and the smaller one for Windows NT.  If you want to dual boot, you need to have them both, but when you start up your computer, you will boot to the XP or Vista, not the NT.

---

### Post by Mash909 on 2009-11-09
Thanks.

I'm now looking for specific advice on how to proceed with the re-partitioning exercise.

Based on the above, what exactly do I need to do with GParted in order to get a partition suitable for Ubuntu installation?

---

### Post by Mash909 on 2009-11-11
Can anyone offer any help to get me started?
Are there more suitable forums to post my questions?

thanks

---

### Post by Bartender on 2009-11-11
Mash -
You need to find out absolutely for sure which of those damned Dell partitions you need and which you don't.

Dell has a forum with a Linux section.  Or you can search your exact model here, or google it.  Notebook Forums has active Dell and Linux sections.   

Have you made recovery discs yet?  If so, then I *think* you can dump the "Backup" partition, but maybe not because I don't know what that "Dell Restore" partition does.

But people who have Dells and have installed Linux can tell you.  If it were me, I'd try to get rid of everything past sda2 but I don't know for sure how the Dell recovery works.

---

### Post by seenthelite on 2009-11-11
I have a Dell Laptop and have now got it dual booting XP and Ubuntu, works well, I agree use G parted and delete sda 4 and 5. Then when you install Ubuntu put it in the largest free space. The installation will take care of the rest.

---

### Post by Mash909 on 2009-11-13
Thanks all for the advice.

I used GParted to delete the /dev/sda4 and /dev/sda5 partitions, rebooted and selected to install Ubuntu into the available space and it worked a treat.

So much for Friday 13th

:p

---

