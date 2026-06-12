---
title: "Cannot mount volume?!?!!?"
date: 2008-09-04
forum: General Help
---

### Post by skeetwood-mac on 2008-09-04
after a couple months of finally running hardy without too many major problems I ran into this today. I tried to mount one of my ntfs hard drives and I got an error. Cannot mount volume. $logfile indicates unclean shutdown failed to mount  dev/sda1': Operation not supported mount is denied because ntfs is marked to be in use.

so I typed   mount -t ntfs-3g/dev/sda1/media/storage -o force

and got this



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


This makes no sense to me.

---

### Post by Peter09 on 2008-09-04
If this is an XP system disk then it may be that you hibernated the system, or did not shut it down properly. You will need to boot ito XP and shutdown again.

---

### Post by drs305 on 2008-09-04
> **skeetwood-mac said:**
> 

so I typed   mount -t **ntfs-3g/dev/sda1/**media/storage -o force


If that is exactly how you entered it you forgot a space between ntfs-3g and /dev/sda1. Depending on permissions, you also may not be permitted to mount the device without using "sudo".

```
*sudo* mount -t ntfs-3g /dev/sda1 /media/storage -o force
```

---

### Post by skeetwood-mac on 2008-09-13
hey thanks a lot. I put that code in and said it couldn't moun t because the directory didnt exist, but then I tried to  mount the drive normally and it worked. I couldn't boot back into windows and shutdown again because as soon as windows would start to boot the computer would just restart. I've had that problem with windows before. I don't know what causes it though.

---

