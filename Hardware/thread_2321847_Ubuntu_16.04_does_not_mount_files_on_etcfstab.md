---
title: "Ubuntu 16.04 does not mount files on /etc/fstab"
date: 2016-04-24
forum: Hardware
---

### Post by Andrew F in Australia on 2016-04-24
Couldn't edit title.  Should've been:
**Ubuntu 16.04 does not mount drives on /etc/fstab**

Hi All,

Am having trouble with a new install of 16.04

I've got the following code to mount all drives on startup saved into /etc/fstab

```


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc7 during installation
UUID=84e54b79-8671-4acb-9dbc-f89b17667cf6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=77722c72-92d8-4f7c-be10-ef689657bd24 none            swap    sw              0       0
# manually add drives on startup
/dev/disk/by-uuid/644A37CB4A3798AE/media/music2 ntfs-3g rw,auto,users,exec,async,locale=en_AU.UTF-8 0 0
/dev/disk/by-uuid/1AB4F6FBB4F6D7E9/media/Windows ntfs-3g rw,auto,users,exec,async,locale=en_AU.UTF-8 0 0
/dev/disk/by-uuid/1AB4F6FBB4F6D7E9/media/Data ntfs-3g rw,auto,users,exec,async,locale=en_AU.UTF-8 0 0
/dev/disk/by-uuid/5254436B54435141/media/music ntfs-3g rw,auto,users,exec,async,locale=en_AU.UTF-8 0 0
/dev/disk/by-uuid/622225CC174EF447/media/3TB ntfs-3g rw,auto,users,exec,async,locale=en_AU.UTF-8 0 0


```

This has worked before. 

Is there a syntax change in 16.04?

Don't know if it's part of the problem, but the install was problematic.  I think the install treated the 3TB drive as UEFI and kept the rest as BIOS.
GRUB rescue can not install a boot partition on the 3TB drive.

With thanks in advance for any help you can provide.

Regards,

---

### Post by weatherman2 on 2016-04-24
You need spaces between the device ID and the mount path - for example, in this line
```

/dev/disk/by-uuid/644A37CB4A3798AE/media/music2 ntfs-3g rw,auto,users,exec,async,locale=en_AU.UTF-8 0 0

```

You need a space before /media so it would be:

```

/dev/disk/by-uuid/644A37CB4A3798AE /media/music2 ntfs-3g rw,auto,users,exec,async,locale=en_AU.UTF-8 0 0

```

That is not new - must have been a typo on your new edits.

---

### Post by weatherman2 on 2016-04-24
Also, you will have to create the mountpoints manually before you can have them mounted in fstab - so "/media/music2" won't automatically be created for you.  Instead do this once:

```

sudo mkdir /media/music2

```

but even then, /media isn't a great place to make manual mountpoints.  I prefer to leave /media for devices that you mount with Nautilus - and use /mnt or just any other directory (like making a top-level /DATA or somewhere in /home) to mount stuff in fstab.

---

### Post by Andrew F in Australia on 2016-04-25
Thanks Weatherman

I'd manually created directories initially.

Missed the typo. Couldn't see the forest for the trees.

Tried to mount the 3TB drive, which is, I think, mounted UEFI under BIOS.  Kernel Panic.  Will clean that up later.

Regards,

Andrew F

---

