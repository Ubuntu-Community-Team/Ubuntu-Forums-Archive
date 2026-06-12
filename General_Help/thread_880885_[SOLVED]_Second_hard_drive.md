---
title: "[SOLVED] Second hard drive?"
date: 2008-08-05
forum: General Help
---

### Post by harryliddic on 2008-08-05
If I add a second hard drive to accommodate some large video files and I format the drive in ext3 will the file system see it?

---

### Post by dexter.deepak on 2008-08-05
yes of course !!
you will see it at /dev/sdb or /dev/hdb

you will have to manually mount it everytime, so you should edit the /etc/fstab appropriately.

---

### Post by harryliddic on 2008-08-05
But will the file /home/harry/ bridge the gap?

---

### Post by dbeckwitt on 2008-08-05
You've got to give it a mount point.  Until then, it will be unusable.  
Create a folder (i.e. /media/video)
create a mount point in /etc/fstab (i.e. /dev/sdb    /media/video)
then mount the drive and it will be usable in the /media/video folder you created.

---

### Post by Taxman415a on 2008-08-05
Basically yes. The second drive with be /dev/sdb or /dev/hdb for example and you just choose a mountpoint. The default when you install a system is to mount the first or only partition as /media/sdb1 but I don't know off the top of my head how to re-run the scripts that get run when you install that automatically set up you /etc/fstab file. But you can do it manually.

When you add one or more partitions on the new drive, create mountpoints for them with
```
sudo mkdir /media/sdb1
```
etc, but check the output of fdisk -l first so you know if it is sdb or hdb
Then add a line to /etc/fstab with ```
sudo gedit /etc/fstab
``` that looks like:
/dev/sdb1	/media/sdb1     ext3    defaults        0       2
Then ```
sudo mount -a
``` will mount everything in your fstab, which in this case will just mount the new drive if everything matches.

Technically it is better to run ```
sudo blkid -c /dev/null
``` and place the UUID=foo part (without the quotes) in place of the /dev/sdb1 in the /etc/fstab line above.

---

