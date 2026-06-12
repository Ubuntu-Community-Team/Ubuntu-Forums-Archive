---
title: "Certain folders read-only on mounted FAT32 partition"
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by Rehevkor on 2005-05-09
I have my Windows FAT32 partition mounted through fstab with this line
```
/dev/hda2 	/media/windows  vfat    rw,user,umask=000	0	0
```

I can explore the partition just fine, but many of the folders, such as Program Files and My Music, are read only to me. I want write access to ALL folders and files on the partition from within Ubuntu, but nothing I try gives me that. I tried everything suggested in [this thread](http://www.ubuntuforums.org/showthread.php?t=31337) to no avail.

How can I mount this partition with write access for everything?

---

### Post by brickbat on 2005-05-09
Hi.

I had this problem but it was a few weeks ago and my memory is awful.  Basically what I found was that it was directories that were big (I think bigger than 1GB) that were made read only.

You don't need to do a chown as long as you change the permissions.  Lets say the disk is /media/windows as per your fstab file

I just did 

sudo chmod a+w -R /media/windows

The -R is important because that forces it to do all of the sub-directories and files.  It worked for me.  If it doesn't work for you use the -v flag and see what it is saying.

ciao
bb

---

### Post by poofyhairguy on 2005-05-09
[QUOTE=Rehevkor]
How can I mount this partition with write access for everything?[/QUOTE]

Try opening a superuser nautilus (sudo nautilus) and changing the permissions by hand....

---

### Post by Rehevkor on 2005-05-09
[QUOTE=brickbat]Hi.

I had this problem but it was a few weeks ago and my memory is awful.  Basically what I found was that it was directories that were big (I think bigger than 1GB) that were made read only.

You don't need to do a chown as long as you change the permissions.  Lets say the disk is /media/windows as per your fstab file

I just did 

sudo chmod a+w -R /media/windows

The -R is important because that forces it to do all of the sub-directories and files.  It worked for me.  If it doesn't work for you use the -v flag and see what it is saying.

ciao
bb[/QUOTE]
 Thanks! That did it :)

---

### Post by leep on 2006-12-31
> **poofyhairguy said:**
> Try opening a superuser nautilus (sudo nautilus) and changing the permissions by hand....

I noticed that my "/media/hdc2" fat32 partition is owned by "root" group "root", while other partitions (ntfs amd fat32) are owned by "root" group "plugdev".
I tryed to change group and permissions on this partition, 

sudo chgrp plugdev /media/hdc2
sudo chmod 777 -R /media/hdc2

but I obtain an error. The result is that I got an empty 50 gig partition without being able to write anything on it.

Any idea?

---

