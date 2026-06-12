---
title: "Copying installation to new hard disk"
date: 2008-08-28
forum: General Help
---

### Post by pudding on 2008-08-28
Hi,

Im getting a new 500gb sata HD tomorrow. My ubuntu is currently on an old 60GB IDE hard disk, and a winXP installation on primary SATA, so I am using GRUB to dual boot. I have a second SATA disk connected for backup, so can disconnect this to connect the new drive in order to copy Ubuntu onto it.

I would like to transfer my Ubuntu installation onto my new disk and use that, using the old disk im currently using for data backup. Whats the best way of doing this? Would it be the dd command? Would I need to change the GRUB menu at all?

---

### Post by Taxman415a on 2008-08-28
You may need to get fun and intimate with Grub to the point that you may be better off reinstalling. It's your choice of course if you'd like to learn how to do this, but it might really be a pain. Off the top of my head I'm not sure of the right block size switches to dd, but dd could work for you. It would be something like ```
dd if=/dev/hda1 of=hda1 bs=1k
``` First you'd need to partition the new drive, then copy in the partitions' images. Then you'd need to reinstall grub so that it knows to point to the new boot location. I think that would set up a new menu.lst file, but if not you'd have to edit that so that the lines that read root            (hd1,0) have the right numbers to point to the right partitions. Try the grub howto here: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

Also found a few links quickly googling that may help you. [http://www.inference.phy.cam.ac.uk/saw27/notes/backup-hard-disk-partitions.html](http://www.inference.phy.cam.ac.uk/saw27/notes/backup-hard-disk-partitions.html)
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

The last one may be much easier than using dd.

---

### Post by pudding on 2008-08-29
Thanks for the post. 

So the first step will be to format and partition the new disk? Any recommended programs for this? 

Then 2nd step is to copy the image of the linux install to the new disk. 

When you say I'd need to reinstall GRUB, is that on the new hard disk with Ubuntu on it, or on the WinXP disk in the MBR so that it points to the new disk? Not really sure about this bit, I just let the install of Ubuntu do everything last time.

---

### Post by Voorhees1979 on 2008-08-29
Grab "gparted" its in the package manager so just search for it. Very handy program this will format your drive for you. Use ext3 as the file system. I dont know how to copy over an install. But this will help with the formatting.

---

### Post by Taxman415a on 2008-08-29
> **pudding said:**
> Thanks for the post. 

So the first step will be to format and partition the new disk? Any recommended programs for this? 

Then 2nd step is to copy the image of the linux install to the new disk.

NP. Yes, that is correct. Definitely make sure you have other good backups too. This is all stuff that's easy to screw up. Though if you take images of your partitions and don't erase the partitions before you get the new drive up and running that should suffice.

> When you say I'd need to reinstall GRUB, is that on the new hard disk with Ubuntu on it, or on the WinXP disk in the MBR so that it points to the new disk? Not really sure about this bit, I just let the install of Ubuntu do everything last time.

Read carefully through that Grubhowto. Basically the way it does it is after getting your partitions copied over, you go back through the installer, ignore/skip all the other parts, then you get to the partitioner, reselect your root, swap, and other partitions, but make sure to NOT reformat them, then this allows you to let the installer more or less automatically reinstall Grub for you in the right places. So yes, it will put the needed part in the MBR and the rest where it needs to go on your / partition.

---

### Post by hyper_ch on 2008-08-29
it should be possible to dd your old disk completely to the new disk. That way all information will be stored 1:1. Problem is, that you then only use 60GB. Afterwards you'd need to adjust space with (g)parted or so....

Note: I have never tried it but it should work :)

---

### Post by pudding on 2008-09-09
I have got my new disk in my PC now, and have used Gparted to create new partitions. One of 462GB of ext3, and one of 2GB for the SWAP. When I use  ' sudo dd if=/dev/sdc of=/dev/sdb ' I keep getting this :-

dd: reading `/dev/sdc': Input/output error
304760+0 records in
304760+0 records out
156037120 bytes (156 MB) copied, 19.9809 s, 7.8 MB/s

Any clues? Am I doing this correct?

---

### Post by hyper_ch on 2008-09-09
are you sure the drives are correct?

furthermore, you maybe shouldn't run dd from the drive you copy from or copy to... hence use a live cd

---

### Post by pudding on 2008-09-09
Ok, will boot from CD and try that, thanks.

---

### Post by hyper_ch on 2008-09-09
well, I never tried it myself but it should be working the way dd copies stuff.

---

### Post by pudding on 2008-09-09
Trying from a LiveCD doesnt work either :( This seems a bit tricky.

If I simply do a fresh install, then copy my home folder from the old drive, what will I lose, and what would I have to re-install?

---

