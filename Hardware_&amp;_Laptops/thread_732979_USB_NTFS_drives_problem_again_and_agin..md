---
title: "USB NTFS drives problem again and agin."
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by zz12 on 2008-03-23
I have a problem with an external USB/NTFS drive in Kubuntu 7.10.  I was
using it as read-only for quite some time by just de-selecting the
"mount as user" option in Dolphin.  I did not add anything to /media or
fstab. Worked OK.  The fixed ntfs partitions are also working fine as
read/write.

Now I want to use it as read/write and I have been reading a lot of posts
here but no luck.  This is what I did: 

I created a folder /media/ExtUsb750
lrwxrwxrwx 1 root root        6 2008-02-05 22:04 cdrom -> cdrom0
drwxr-xr-x 2 root root     4096 2008-02-05 22:04 cdrom0
drwxrwx--- 2 root plugdev  4096 2008-03-23 02:18 ExtUsb750
drwxrwx--- 1 root plugdev  4096 2008-03-23 10:23 sda1
drwxrwx--- 1 root plugdev 20480 2008-03-23 10:24 sda2

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=18fad993-06b6-434d-8628-8e77f35d9e44 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=C8BAD05CBAD04898 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=58FAD743FAD71BD6 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=4a792740-367a-4d68-801b-b07278df2605 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
# /dev/sdb1 external USB 750
/dev/sdb1       /media/ExtUsb750     ntfs    auto,user,utf8,umask=0111,dmask=0000 0       0

I added the utf8 options because I have a lot of MP3 in different languages
and with many different accents marks. Should perhaps change later on to a
UUID instead of sdb1 but I suppose that this is not the problem.

Kubuntu detects the drive when plugged in and asks me what to do.
I say open in new window.  Dolphin gives me the following error.

fuse: failed to open /dev/fuse: Permission denied
FUSE mount point creation failed
Unmonting /dev/sdb1 (USB750)

Don't know if it is important but /dev/fuse has permissions crw-rw---- root fuse
Same error if I start Dolphin with sudo. Added myself to the "fuse" group,
no difference.  USB750 is BTW the lable of the drive. Also tried some other
options in fstab.

What I'm trying to do now is "hotplugging" the drive but I can survive if
it only works if the drive is connected at boot.  It is a pity that there
is no simple solution to such a common thing.  Do I have start editing
files etc. just because a friend wants to copy some files from my PC to his
external drive?

A final question, do I need or should I use ntfs-config with 7.10?  Will
that simplify things?  It is currently not installed.
:redface:

---

### Post by zz12 on 2008-03-27
If I do a "sudo mount -a" it mounts.
However, in Dolphin it does not show up in storage media only under
/media/ExtUsb750.  Read/Write works.

Mount tells me:
/dev/sda1 on /media/sda1      type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda2 on /media/sda2      type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sdb1 on /media/ExtUsb750 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096

The first two drives are mounted automatically at boot.

I can only assume that hotplugging and auto mount does not work with external ntfs drives.
Is there a difference between ntfs in 7.10 and ntfs-3g?

It just feels so stupid to open up a terminal window and type in stuff every time I connect or disconnect a usb drive.

---

