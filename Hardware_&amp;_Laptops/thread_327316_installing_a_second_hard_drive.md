---
title: "installing a second hard drive"
date: 2006-12-29
forum: Hardware &amp; Laptops
---

### Post by beezix on 2006-12-29
Greetings.

I've just installed Ubuntu 6.06 on:

hp pavilian 7955
Pentium (R) 4 1.5 GHz/400 processor
Chipset Intel 845
256 MB Ram (to be upgraded soon)
primary hd drive 40 MB

(My first Ubuntu machine was struck by lightning -- true story)

And, I am trying to install a Seagate 120 GB Ultra ATA/100 hard drive as a second/slave drive. I've followed the guide [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) and the tuxfile on editing fstab: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

The new drive has been formated to one ext 3 partition and it is recognized by the system in administration/disks and the file browser. 

However, I can not get the disk to mount when the system is booting, or it is mounted by I can't seem to communicate with it.

Here is the fstab text, with the new line created for the second hard drive (hdb1)

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /       ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hdb1       /backup         ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw    0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0   0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0   0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

One possible problem is that I could not edit fstab even as "root" so I did chmod to make fstab read-writable, and have not re-set the permissions (how is that done?)

When I double click on the drive icon in file-browser I get this error message:
error: device /dev/hdb is not removable

error: could not execute pmount

When I give the line command to mount the second hard drive I am told that the drive is already mounted.

When I try to copy a document to the secondary hard drive I get the error message:

Error "Invalid URI" while copying.

Many thanks for any thoughts on this.

---

### Post by teaker1s on 2006-12-29
[http://ubuntuguide.org/wiki/Ubuntu_dapper]("http://ubuntuguide.org/wiki/Ubuntu_dapper")
also a link to edgy on above page

---

### Post by beezix on 2007-01-01
Well, I was wanting to get on with life so bypassed the original drive and am using the new drive for operating system and storage -- simple it good, sometimes.

Thanks

---

