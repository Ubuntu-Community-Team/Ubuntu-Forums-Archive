---
title: "[SOLVED] Formatting a hard disk"
date: 2008-04-27
forum: Hardware
---

### Post by bilijoe on 2008-04-27
I guess this is a hardware issue.:)  I recently installed a hard disk, salvaged from one of my many dead Windows machines, into my delightfully easy to use Ubuntu-Linux machines.  The HDD has an NTFS file system on it, and an old copy of XP.  I want to just wipe it clean, and add it to the [disk] storage space for my Linux system.  How do I perform a [simple(?)] format on the newly installed disk.  Ubuntu sees the disk, and can mount and read it with no problem, so I have access to it.  Where do I go from here?

---

### Post by Patb on 2008-04-27
```
sudo umount /dev/your-new-disk
sudo gparted
```
In Gparted, find the partition/s which occupy your new disk, delete them, then create new partition/s formatted to Linux ext3 format.  

Then Apply the changes, (that is, if you are quite sure :)). Close Gparted and reboot. 

Cheers, Pat.

---

### Post by bilijoe on 2008-04-27
I'm sorry, Patb, but your directions are too simplistic for me.  First of all, my system did not respond to the "gparted" command, and I couldn't find it, using "help" or "info" "gparted", or "man" or "man -k", so I don't know what to do there. Second, I did an "ls" of "/dev" and saw a lot of entries, but not one that I could particularly identify as the HDD in question.  Thanks anyway.

---

### Post by SnakeHips on 2008-04-27
```
sudo fdisk -l
```

and 

```
mount
```

will give you the information you need

and search synaptic for "gparted".....

---

### Post by bilijoe on 2008-04-27
Well, I thought I had it figured out.  I added and then ran gparted.  After a little poking around, I found out how to get the new disk to show.  I deleted the NTFS partition, and created a new partition. The default filesystem type was ext2, so I created and formatted it as ext2.  Everything looked good, so I closed gparted, and went to "computer", under "Places".  There was no longer an entry for the new HDD, so I assumed it had been integrated into "filesystem", but I opened that, and there's no evidence of the new drive (i.e., the total size is the same as it was, and there's no indication of a second drive or new partition).  So where'd my second HDD go?  And how do I access it?

---

### Post by Patb on 2008-04-28
Sorry if I was too cryptic Bili.  To find out the device name of the new disk try (as Snakehips says):
```
sudo fdisk -l
```
Let's say you find it is on "/dev/sdb1".  To mount the disk, you would make a directory where you want it to appear (ie to be mounted) and mount it there eg:
```
sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1
```
To make this permanent for every time you boot, you would need to edit your fstab file and put in an appropriate line.  
```
sudo gedit /etc/fstab
```
Take care with this file - don't tinker with existing entries unless you know what you are doing.  Put the new line at or towards the bottom.  Here is an example of two such lines from my fstab:
```
/dev/sdb1   /media/sdb1     ext3    defaults        0       2
/dev/sdb3   /media/sdb3     ext3    defaults        0       2

```
In this example, fstab, which is read during the boot process, mounts the device /dev/sdb1 on the directory /media/sdb1 and so on.  My second hard drive has two partitions which are  recognised as devices /dev/sdb1 and /dev/sdb3 respectively.  I created the directories /media/sdb1 and /media/sdb3 and that is where the contents of those two directories appear on my file manager.  You should use ext2 instead of ext3 if that is the format you have used.  I'm not certain it matters, but put an extra empty line at the end of the file.

If you want to know more about the parameters in these lines, "man fstab".  

If you have any further questions, please post.  Cheers, Pat.

---

### Post by SnakeHips on 2008-04-28
> **bilijoe said:**
> Well, I thought I had it figured out.  I added and then ran gparted.  After a little poking around, I found out how to get the new disk to show.  I deleted the NTFS partition, and created a new partition. The default filesystem type was ext2, so I created and formatted it as ext2.  Everything looked good, so I closed gparted, and went to "computer", under "Places".  There was no longer an entry for the new HDD, so I assumed it had been integrated into "filesystem", but I opened that, and there's no evidence of the new drive (i.e., the total size is the same as it was, and there's no indication of a second drive or new partition).  So where'd my second HDD go?  And how do I access it?

You might like to consider ext3 as the filesystem type (just reformat) ,it's basically ext2 +  supports journaling and is considered more the "norm".

---

