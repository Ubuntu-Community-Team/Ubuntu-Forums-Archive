---
title: "Mount drives for all users"
date: 2009-04-06
forum: Hardware
---

### Post by Dooley on 2009-04-06
I have an acer aspire one(netbook) and wish to mount both mmc slots to be read/write/executable for all users.

I've tried several /etc/fstab configs, none of which worked or required me to have to chmod each time I booted. Then there's issue with the fact that I could read and write to the mounted folder but could not create symbolic links, then sometimes I could and they would work.......

So what I'm looking for is basically a modification of my /etc/fstab to allow all users full access to the the 2 drives on bootup.

This is the latest config I have however it's doesn't seem to work at all.

```

/dev/mmcblk0p1 /home/complete   vfat    silent,umask=0,locale=en_US.utf8        0       0
/dev/mmcblk1p1 /home/filez      ext2    silent,umask=0,locale=en_US.utf8        0       0

```

I would be very appreciative of any solutions available, this has been a problem that's been plaguing me since I started using linux and have yet to discover an appropriate solution.

Thanks!
Dooley

---

### Post by Dooley on 2009-04-07
Anyone have a solution for this? I'd imagine it fairly common request, it's just one of those things I can't seem to get my head around.

Thanks!

---

### Post by kpkeerthi on 2009-04-07
Are your sure **/dev/mmcblk0p1** is correct? What does ```
sudo fdisk -l
``` print?

Also the mount options (silent,umask=0,locale=en_US.utf8 in your case) cannot be the same for different filesystems. 

See [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) for more information.

EDIT: I missed these were MMC

---

### Post by vanadium on 2009-04-07
If it is ubuntu youhave on this notebook, these removable devices would not need to be mounted using /etc/fstab. They should be automatically mounted with permissions for the current user.

---

### Post by Dooley on 2009-04-07
Hi thanks for the responses


kpkeerthi, sudo fdisk -l produces 
```


Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7d8b185

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7494291   83  Linux
/dev/sda2             934         981      385560    5  Extended
/dev/sda5             934         981      385528+  82  Linux swap / Solaris



```

However when I run df -h

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             7.1G  5.7G  1.1G  85% /
tmpfs                 499M     0  499M   0% /lib/init/rw
varrun                499M  352K  499M   1% /var/run
varlock               499M     0  499M   0% /var/lock
udev                  499M  2.7M  497M   1% /dev
tmpfs                 499M  104K  499M   1% /dev/shm
lrm                   499M  1.8M  498M   1% /lib/modules/2.6.27-9-generic/volatile
tmpfs                 499M  752K  499M   1% /var/log/apt
tmpfs                 499M  752K  499M   1% /var/log
tmpfs                 499M   44K  499M   1% /tmp
tmpfs                 499M     0  499M   0% /var/tmp
/dev/mmcblk0p1         15G  2.5G   13G  17% /home/complete
/dev/mmcblk1p1        3.8G  1.6G  2.0G  44% /home/filez

```

vanadium, your right the drives do appear when taken out of the fstab. However I was trying to give them static mount points by right clicking on them on the desktop and changing the mount point however now it seems I get an error saying invalid mount option and I've no idea how to change the mount points back via gnome and not fstab.


Thanks again,
Dooley

---

### Post by vanadium on 2009-04-08
The mount point you provide in the right-click menu can only be a single label, not a pathname. Unfortunately, the dialog does not check for the validity of the entry.

A better approach to control the name of the mount point is to label the drive. As an additional benefit, this approach will make your drive mount with the same name on any Ubuntu system. See [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive) on how to label a partition.

---

### Post by Dooley on 2009-04-08
Thanks for the link vanadium,

I renamed the labels as you suggested, how they still won't mount, same error as usual. Basically I right-clicked on the cards on the desktop and changed what I thought was the mount point. Now when I try mount them it says something like "/" isn't a valid entry. I can't find the GUI tool in Gnome to stop this.

The storage device manager doesn't seem to detect them either.

Any way to circumvent these annoying guis with an fstab config?

---

### Post by axisthelimitless on 2009-04-08
Alright, I am incredibly new to Ubuntu and am currently running Hardy. Previously I was running Ubuntu and everything was running perfectly but I became frustrated by not being able to update my ipod or play many games (after having read a million and one threads on how to do just that) So I installed XP in an attempt to dual boot. Immediately thereafter my Ubuntu started acting very buggy so I deleted both partitions and gave myself a fresh install of Hardy. Now I can not mount two of my hd and after again reading many threads I can not get it to work. I am fairly sure that in trying so many things I have only made matters worse. Even after trying both choices presented by the os itself. In conclusion I could really use some assistance p & t.

Response to sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8cdf446

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13721371

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4660    37431418+  83  Linux
/dev/sdb2            4661        4865     1646662+   5  Extended
/dev/sdb5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
240 heads, 63 sectors/track, 32422 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xaa0de88d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       32422   245110288+   7  HPFS/NTFS

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00009ac8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       19457   156288321    c  W95 FAT32 (LBA)

Disk /dev/sde: 528 MB, 528744448 bytes
17 heads, 60 sectors/track, 1012 cylinders
Units = cylinders of 1020 * 512 = 522240 bytes
Disk identifier: 0x00978b1a

   Device Boot      Start         End      Blocks   Id  System

Response to Mount attempt via mount -t ntfs-3g /dev/sda1/media/Alexxx 233_-o force

Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by vanadium on 2009-04-08
@Doolay: it is in the properties of the drive that you need to remove the entry that you have put there. Then next time you attempt to mount the drive, it should take the default name, which is the label of the volume, and if not, a generic name based on the size such as "30 GB Volume".

@axisthelimitless: Welcome to this forum. However, please realize that you are what we call "hijacking" a thread. Feel free to open a new thread for your particular problem.

---

### Post by Dooley on 2009-04-08
Hey vanadium,

Yeah where exactly is that setting in Computer when I right click and choose properties, nothing comes up?


Thanks
Dooley

---

### Post by vanadium on 2009-04-09
Right-clik drive, then properties, Drive tab or volume tab, settings. I understand that the settings under Drive tab are global for the connection, while these might be overriden for specific drives (volumes) by the settings on the volume tab. Delete any entry you made for "Mount point".

---

