---
title: "mounting fat32 drive"
date: 2005-09-12
forum: Hardware &amp; Laptops
---

### Post by plefno on 2005-09-12
I'm trying to mount a fat32 partition so that my main user has ownership of all files on the partition.  Apparently I currently have it mounted such that root has ownership, and it won't allow me to change ownership to my user (cbecker) by using chown.  Can anyone tell me what my entry in /etc/fstab should be such that cbecker has ownership but all other users can also have read access as well.  Thanks a lot.

---

### Post by jasmuz on 2005-09-12
Editing Ubuntu's filesystem table (Taken from the wiki.ubuntu.org) [https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions)

It is possible to break Ubuntu if some of the earlier lines in the file opened during this step are modified, so be sure to read this section carefully.

Run the following command to open Ubuntu's filesystem table in a text editor.

sudo gedit /etc/fstab

The file opened contains lines of the form <device> <location> <Linux type> <options> <dump> <pass>. Every element in this line is separated by whitespace (spaces and tabs).

'options' is a string of options which should be applied to the partition when it is loaded. The following table should help in the decision of what options to use.

Description
	

FAT(16|32) partition
	

NTFS partition*
	

Apple Partition

Accessible by everyone
	

user,auto,fmask=0111,dmask=0000
	

ro,auto,user,fmask=0111,dmask=0000
	

user,auto,file_umask=0111,dir_umask=0000

Accessible by a subset of users**
	

user,auto,fmask=0177,dmask=0077,uid=1000
	

ro,user,auto,fmask=0177,dmask=0077,uid=1000
	

user,auto,file_umask=0177,dir_umask=0077,uid=1000

---

### Post by plefno on 2005-09-12
Thanks, that wiki helped.  I had some of those options set when I was mounting the drive, but apparently one of the ones i didn't have was the problem.  Anyway, thanks.

---

