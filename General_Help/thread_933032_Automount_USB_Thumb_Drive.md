---
title: "Automount USB Thumb Drive"
date: 2008-09-29
forum: General Help
---

### Post by DapperMe17 on 2008-09-29
I'd like to use a thumb drive to Grsync a few folders to. I would like the thumb drive to automount with root permissions at startup. 

The USB drive includes a FAT32 partition & Ext3 partition.

My "mtab" entries for the two partitions looks like this...


/dev/sdb1 /media/disk vfat rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000 0 0
/dev/sdb2 /media/disk-1 ext3 rw,nosuid,nodev,uhelper=hal 0 0



Do I need to add something to "fstab"?

Also, I would like to change the names of those folders to something besides "disk" & "disk-1"...should I just do this in the "mtab" file?

---

### Post by Herman on 2008-09-29
> Also, I would like to change the names of those folders to something besides "disk" & "disk-1"...should I just do this in the "mtab" file? I don't know how you would do that.
I prefer to give my file systems their own labels as explained in the following links,

[Make a label for your ext3 file system]("http://users.bigpond.net.au/hermanzone/p10.htm#ext3_usbdisk_labelling") - give your ext3 file systems descriptive names

[FAT32 usbdisk volume label]("http://users.bigpond.net.au/hermanzone/p10.htm#fat32_usbdisk_volume_label") give your FAT32 usbdisk a pet name

> I would like the thumb drive to automount with root permissions at startup. 
The USB drive includes a FAT32 partition & Ext3 partition.
My "mtab" entries for the two partitions looks like this...
/dev/sdb1 /media/disk vfat rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,u  id=1000 0 0
/dev/sdb2 /media/disk-1 ext3 rw,nosuid,nodev,uhelper=hal 0 0
Do I need to add something to "fstab"?I think so, see [How to fstab]("http://ubuntuforums.org/showthread.php?t=283131"), by bodhi.zazen

Regards, Herman :D

---

### Post by DapperMe17 on 2008-09-29
Thanks Herman!

---

