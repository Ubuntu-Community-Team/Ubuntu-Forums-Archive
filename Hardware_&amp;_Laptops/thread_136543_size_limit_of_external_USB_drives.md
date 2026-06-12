---
title: "size limit of external USB drives?"
date: 2006-02-26
forum: Hardware &amp; Laptops
---

### Post by schatz on 2006-02-26
I'm having problems mounting an external 300GB USB FAT32 formatted disk.

If I simply boot and turn the external drive on, Ubuntu seems not to recognize the disk correctly. 
sudo fdisk -l shows:
total 24
drwxr-xr-x   6 root root 4096 2006-02-25 13:14 .
drwxr-xr-x  22 root root 4096 2005-12-18 12:49 ..
lrwxrwxrwx   1 root root    6 2005-12-17 17:35 cdrom -> cdrom0
drwxr-xr-x   2 root root 4096 2005-12-17 17:35 cdrom0
drwxr-xr-x   2 root root 4096 2005-12-17 17:35 cdrom1
lrwxrwxrwx   1 root root    7 2005-12-17 17:35 floppy -> floppy0
drwxr-xr-x   2 root root 4096 2005-12-17 17:35 floppy0
drwxr-xr-x   2 root root 4096 2006-02-25 13:14 sda1

ls -la /media/
total 24
drwxr-xr-x   6 root root 4096 2006-02-25 13:14 .
drwxr-xr-x  22 root root 4096 2005-12-18 12:49 ..
lrwxrwxrwx   1 root root    6 2005-12-17 17:35 cdrom -> cdrom0
drwxr-xr-x   2 root root 4096 2005-12-17 17:35 cdrom0
drwxr-xr-x   2 root root 4096 2005-12-17 17:35 cdrom1
lrwxrwxrwx   1 root root    7 2005-12-17 17:35 floppy -> floppy0
drwxr-xr-x   2 root root 4096 2005-12-17 17:35 floppy0
drwxr-xr-x   2 root root 4096 2006-02-25 13:14 sda1

However,
ls -la /media/sda1/
total 8
drwxr-xr-x  2 root root 4096 2006-02-25 13:14 .
drwxr-xr-x  6 root root 4096 2006-02-25 13:14 ..
-rw-------  1 root root    0 2006-02-25 13:14 .created_by_pmount

There ARE many files on that disk, But Ubuntu cannot see them.

So I decided to update the /etc/fstab to mount the disk without mount or pmount.
If I boot with: 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#### added this entry for USB #####
/dev/sda1      /media/sda1     vfat    rw,umask=000,users      0       0

ls -la /media/
total 24
drwxr-xr-x   6 root root 4096 2006-02-25 13:14 .
drwxr-xr-x  22 root root 4096 2005-12-18 12:49 ..
lrwxrwxrwx   1 root root    6 2005-12-17 17:35 cdrom -> cdrom0
drwxr-xr-x   2 root root 4096 2005-12-17 17:35 cdrom0
drwxr-xr-x   2 root root 4096 2005-12-17 17:35 cdrom1
lrwxrwxrwx   1 root root    7 2005-12-17 17:35 floppy -> floppy0
drwxr-xr-x   2 root root 4096 2005-12-17 17:35 floppy0
drwxrwxrwx   2 root root 4096 2006-02-25 13:14 sda1

ls -la /media/
shows all files of the harddisk.

However, when I try to access the files on the external USB disk, it sometimes takes a couple of seconds, 10 to 20 seconds, to show the content of the folders. 

Has anyone mounted an external FAT32 USB disk with 300GB?

---

