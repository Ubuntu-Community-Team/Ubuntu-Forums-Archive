---
title: "External harddrive: Mount and format?"
date: 2010-05-29
forum: Hardware
---

### Post by Melindrea on 2010-05-29
This is not so much a question (and I might very well be in the wrong forum, I feel like I don't have enough knowledge at this point to properly know what it is I'm needing), as trying to figure out if something that I think is practical, really would be.

I have all my music on an external harddrive, which at this point is in NTFS-format. I'm considering finding a way to mount it "permanently" (or at least more-or-less so - it will be brought along when we have just the laptop, but otherwise it's connected to my tower), and to reformat it to one of the linux formats (I think it's ex3 that seems to be most stable from what I've read up on).

Is this feasible? Would I gain anything from doing this? And do you have any suggestions on where to look for the "permanently mounting" bit?

---

### Post by srs5694 on 2010-05-29
You can certainly change the filesystem from NTFS to something more Linux-centric; however, doing so will erase all the files on the disk. Therefore, if you want to do this, you should first back up everything on the disk. If this is impossible, you should make it possible, since hard disks can and do fail on occasion, and it sounds like it would be a major problem to re-create all those files.

Changing to a Linux-specific filesystem has advantages if you seldom or never use the drive with a Windows system, since Linux-specific filesystems are likely to perform better than NTFS under Linux and because Linux lacks good NTFS maintenance tools. The latter point means that you can easily lose access to the drive in Linux after a power failure or system crash, and if this happens you won't be able to access the drive until you've plugged it into a Windows system and shut it down properly.

As for permanently mounting it, you can create an entry in /etc/fstab. Something like this should do the trick:

```

/dev/sdb1        /home/media        ext3        users    0 0

```

You should change /dev/sdb1 to the appropriate device for your system, or use a UUID specification instead. (You can find the correct UUID with the blkid utility. Be sure to do this *after* you create a new filesystem on it.) This example mounts the disk at /home/media, but you can change that to something else if you like. Whatever it is, it must exist as an ordinary directory before you begin. The "users" option enables ordinary users to mount and unmount the disk, if necessary.

---

### Post by Melindrea on 2010-05-29
I'm not quite inept enough to think that I don't need to backup the files. =) They'll all be moved over to the laptop while I do this, of course.

Is there a reason to use Ex4 rather than ex3?

Also, does it need to be put into the same USB port, or would this setup find it automatically when I put it in?

Thanks for your response.

---

### Post by Melindrea on 2010-05-30
Bump?

---

### Post by sidzen on 2010-05-30
I.
Recommend you explore this site for what you're looking for:
[http://manual.sidux.com/](http://manual.sidux.com/)
Also,
[https://help.ubuntu.com/](https://help.ubuntu.com/)        is good, too.

II.
RE: file system
ext4 is used by default for most all 2010 linux distros, including Slackware.

---

### Post by Melindrea on 2010-05-31
Thanks.

I'd heard that there might be some instabilities with ext4, which is why I wonder.

---

### Post by dino99 on 2010-05-31
no need to build headhaches, follow the easy way:

linux is able to deal with ntfs: search "ntfs" into synaptic and install: ntfsprogs, ntfs-3g, libntfs-3g75, libntfs10

mountmanager deals with partitions and devices, install it and set your prefs (system admin mountmanager)

---

### Post by vanadium on 2010-05-31
My five cents:

* the "less" easy route to convert to ext 4 or ext 3 is by far preferred for reasons given by srs5694: performance , stability and reliability.
* In my opinion, there is never a reason to mount an USB drive through /etc/fstab. Give the partition a meaningfull label. Then, Ubuntu will automatically use the partitions label as name for the mount point under "/media". The drive will automatically be mounted under the same mount point on every Ubuntu system you connect it to.
* ext4 is proofed by now, and the default on many distributions. It performs faster than its predecessor. Only compatibility with older linux systems would make you go for ext3. Otherwise, ext4 is the best choice.

---

