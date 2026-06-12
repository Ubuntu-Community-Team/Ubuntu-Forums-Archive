---
title: "Invalid mount option when attempting to mount the volume"
date: 2009-08-23
forum: Hardware
---

### Post by EclipseOTO on 2009-08-23
So, I've been trying to figure out how to mount my other 2 partitions as soon as I log in to no avail.  In fact, I made more trouble...  Now I can't even access the files on the drive outside of going and mounting them manually (earlier I could just click on the fs and it would mount).  I get the error "Invalid mount option when attempting to mount the volume."  I changed a few settings under the volume properties, how do I change them back???

Also here's the fstab file:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=0b53eb1b-2b78-4b87-9dda-7b46722e9bd2 /               ext3    


Thanks for the help ya'll!

---

### Post by drs305 on 2009-08-23
> **EclipseOTO said:**
> 

Also here's the fstab file:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=0b53eb1b-2b78-4b87-9dda-7b46722e9bd2[COLOR="DarkRed"] /               ext3  [/COLOR]  


Thanks for the help ya'll!

First, change the root fstab to:
> UUID=0b53eb1b-2b78-4b87-9dda-7b46722e9bd2 / ext3  relatime,errors=remount-ro 0 1

For the other partitions, please give us the desired mount points and the results of:
```

sudo blkid

```

---

### Post by EclipseOTO on 2009-08-23
Thanks,

The results of the blkid was 

/dev/sda1: UUID="0b53eb1b-2b78-4b87-9dda-7b46722e9bd2" TYPE="ext3" 
/dev/sda2: UUID="486409C101C157CF" TYPE="ntfs" 
/dev/sda3: UUID="4A4F-908A" TYPE="vfat"

---

### Post by drs305 on 2009-08-23
> **EclipseOTO said:**
> Thanks,

The results of the blkid was 

/dev/sda1: UUID="0b53eb1b-2b78-4b87-9dda-7b46722e9bd2" TYPE="ext3" 
/dev/sda2: UUID="486409C101C157CF" TYPE="ntfs" 
/dev/sda3: UUID="4A4F-908A" TYPE="vfat"

Here would be the standard entries for automounting in fstab. Mount points of /media will be displayed on the Desktop. Mount points in /mnt will not. /mnt is the more traditional location for non-removeable drives, but it really is a matter of personal preference.

Make the mount points and make yourself the owner (examples later assume you are user 1000, check with command "id"):
```

sudo mkdir /mnt/XXX /mnt/YYY /mnt/ZZZ
sudo chown -R *[COLOR="DarkRed"]yourusername[/COLOR]*: /mnt/XXX   /mnt/YYY  /mnt/ZZZ

```

vfat:
> 
UUID=4A4F-908A /mnt/XXX vfat auto,users,uid=1000,umask=027,utf8 0 0


ntfs:
> 
UUID=486409C101C157CF /mnt/YYY ntfs-3g auto,users,uid=1000,umask=027,utf8 0 0


ext:
> 
UUID=0b53eb1b-2b78-4b87-9dda-7b46722e9bd2 /mnt/ZZZ ext3 defaults  0 2


---

### Post by EclipseOTO on 2009-08-23
hmm I keep getting "bash: /mnt/Shared is a directory" (shared is my XXX)  Should I have actually used XXX or am I doing something wrong?

---

### Post by EclipseOTO on 2009-08-23
Wait, nevermind, that's supposed to go in the fstab I'll bet.  Thanks!

---

