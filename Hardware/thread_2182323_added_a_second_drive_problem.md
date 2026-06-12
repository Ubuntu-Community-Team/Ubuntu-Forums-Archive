---
title: "added a second drive problem"
date: 2013-10-20
forum: Hardware
---

### Post by jgw on 2013-10-20
I have added a new drive.  I have also reformatted it.  It will be a data drive and it is a 2tb drive.

I have also added the following to the last line of the fstab file.
UUID=40b93957-381c-47fa-a615-80af81d14b44  /media/drive2  ext4    defaults   0 2

The drive appears as "drive2" in media
It also appears as 2.0 tb filesystem  in file manager

It sometimes mounts, sometimes does not mount, and sometimes does not want to mount
It also doesn't want to open any specific files as the permissions are screwed up

So, it looks as if I have cleverly really screwed things up.  Before I start messing with chmod I thought I would seek some thoughts from others as to what I should really be doing (instead of foraging ahead and well and truly screwing things up)

Any thoughts would be helpful - thank you......

---

### Post by mkmanifesto on 2013-10-20
So as of right now you have no data on the the 2nd drive and if so the only thing I can think of doing that may help would be fdisk. I had to use fdisk on one of my drives to fix some problems I was having because for one reason or another it was stuck using a different file system.

---

### Post by oldfred on 2013-10-21
If an external or USB drive it may not have come up to speed in time to be mounted correctly. They keep improving boot time and then an external drive may not be fully up to speed.
If external and separate power supply make sure it is on and running before booting.

You may need to remove entry from fstab and add a script at end of boot or to let you manually add it after boot.
Or aAll you have to run is this to remount fstab if it only does not work occassionly.
sudo mount -a

You will need to set ownership & permissions on your partition.
This example assumes it is not mounted and then you manually mount at /mnt/data, you can change to your mount.
Note that -R is recursion and all files & folders will be changed. Do not run on any system partition or you will have to reinstall as changing system ownership & permissions is just about impossible to restore.

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo fdisk -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

---

### Post by jgw on 2013-10-21
Thanks for the replies!

I obviously didn't explain my situation properly and I apologize.  The drive has been formatted and has a single partition (ext4).  When I did all that it got put into media instead of mnt.  Now, to get it into mnt should I remove it from media?  

the current description, from "sudo lshw -C disk":
  description: ATA Disk
       product: WDC WD20EVDS-63T
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: 01.0
       serial: WD-WCAVY6774192
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00013abd
The drive is actually sdb1 (single partition) Its no problem disconnecting, rebooting, doing whatever, reconnecting, etc.  

The results, for the drive in question, after "sudo fdisk -l" is:
Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00013abd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907028991  1953513472   83  Linux

I guess I should also mention that I am familiar with fdisk have used it for a long time beginning with dos (been at this stuff for a while <g>)

anyway, should I remove the drive from /media, redo the line in fstab (I wonder if 'default' really belongs in that line) and then, starting with the mkdir in mnt proceed with the rest of the commands?  Last time I just bulled ahead, this time I am trying to take this step by step <g>

Thank you...........

---

### Post by oldfred on 2013-10-21
It does not really matter where you mount it. There are a lot of arguments over which is correct and it is not clear.

/media should be ok for an external drive. I use /mnt for internal drives.
The main difference used to be whether it was shown a second time in Nautilus left panel or not. In /media it used to show with an underscore at the end as a second mount and that would not work as it was already mounted.

Is drive always connected?
 Mounting with fstab does not like it if not connected an booting, but usually just gives a message & lets you continue.

---

### Post by jgw on 2013-10-21
Thanks for the replies!

I obviously didn't explain my situation properly and I apologize.  The drive has been formatted and has a single partition (ext4).  When I did all that it got put into media instead of mnt.  Now, to get it into mnt should I remove it from media?  

the current description, from "sudo lshw -C disk":
  description: ATA Disk
       product: WDC WD20EVDS-63T
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: 01.0
       serial: WD-WCAVY6774192
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00013abd
The drive is actually sdb1 (single partition) Its no problem disconnecting, rebooting, doing whatever, reconnecting, etc.  

The results, for the drive in question, after "sudo fdisk -l" is:
Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00013abd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907028991  1953513472   83  Linux

I guess I should also mention that I am familiar with fdisk have used it for a long time beginning with dos (been at this stuff for a while <g>)

anyway, should I remove the drive from /media, redo the line in fstab (I wonder if 'default' really belongs in that line) and then, starting with the mkdir in mnt proceed with the rest of the commands?  Last time I just bulled ahead, this time I am trying to take this step by step <g>

I just rebooted to make sure.  The drive is in unity as "2.0 tb Filesystem".  It is also in the file manager as "/media/drive2".  My suspicion is that it needs to be in one place as one name but that may make no difference.  If what I have will work then all I have to do is to set the permissions?  (I think part of my confusion lies in the permission errors which kinda look like things are not mounted.  Then I try and mount and it tells me that there is something already going on.  When I rebooted I checked to see if I was really mounted - I was.  I think I have two choices - remove everything and start over or deal with the permissions although having the same drive, as two different names, makes me a little edgy.  

Thank you...........  Thoughts?

---

