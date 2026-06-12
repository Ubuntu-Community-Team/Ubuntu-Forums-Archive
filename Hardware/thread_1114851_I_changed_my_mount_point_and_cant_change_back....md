---
title: "I changed my mount point and cant change back..."
date: 2009-04-03
forum: Hardware
---

### Post by homerwookey on 2009-04-03
Hi all, after spending a good few hours trying to work this out I have to ask you all for help, I have a problem similar to Werries, posted may 2008 I altered the mount point of my media player using GUI and included the / so I can not now access the volume tab in places-computer-walkman-properties to change it back, and of course I cant mount the drive now. I get the message 'unable to mount the volume 'WALKMAN'. mount point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)
Could someone please talk me through how to rectify this as I have become very confused!
Thanks
Edit: I did try editing fstab  but not very confident with it, and after I added another line '/dev/sdb1 /media/data2 vfat defaults,user,dmask=027,fmask=137 0 0' to the end and rebooted, the message I got was 'unable to mount the volume 'WALKMAN' WALKMAN does not exist' So I deleted line and hence the reason I am here! I have spent a while trying to find answers on the forums but nothing specific to my problem.
If this may help this is the output from fsdisk -l:
paul@dell-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2               9         661     5245222+   b  W95 FAT32
/dev/sda3   *         662       59573   473210640   83  Linux
/dev/sda4           59574       60801     9863910    5  Extended
/dev/sda5           59574       60801     9863878+  82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 3930 MB, 3930587136 bytes
238 heads, 63 sectors/track, 128 cylinders
Units = cylinders of 14994 * 2048 = 30707712 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         128     3838450    b  W95 FAT32

Its the sdb1 which is my media player so I believe ubuntu knows it exists but wont mount

EDIT got it sorted thanks to this guy- dont know how to quote his post but copied it to this thread if anyone else having probs
Thanks MPGARATE

 [SOLVED] change mount point of an unmounted device
I tried to change the mount point of my ipod, and failed. When i connect it I receive an error saying
Quote:
unable to mount volume.
mount_point cannot contain the following characters: newline, G_DIR_SEPERATOR,usually /
can someone please help?

edit: solved by

running gconf-editor

deleting my entry for /system/storage/drives/_org_freedesktop_Hal_devices_voume_uuid_*/mount_point

(or something close to that name)

then i ejected and mounted
__________________
FIX the FLASH CRASH - Laptop Specs - Power Pirate
Last edited by mpgarate; August 29th, 2008 at 05:06 P

---

### Post by homerwookey on 2009-04-08
BUMP just to say thanks

---

### Post by ChuckLife on 2009-04-13
Worked for me as well:p

---

### Post by openess on 2009-06-11
You just saved my day..

this was a tricky one

---

