---
title: "Any filesystems support 'pooled storage' besides ZFS?"
date: 2008-10-29
forum: General Help
---

### Post by shaggy999 on 2008-10-29
I'm looking to set up a file system that I can 'grow' just by adding an extra drive. I know ZFS supports this, but I am not interested in using the FUSE module under development. I just want something similar in functionality to the JBOD RAID option that I can grow as I add drives. Is there anything out there?

---

### Post by ryanhaigh on 2008-10-29
[http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux](http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))
[http://tldp.org/HOWTO/LVM-HOWTO/](http://tldp.org/HOWTO/LVM-HOWTO/)

---

### Post by shaggy999 on 2008-10-29
Ok, but there's one part I don't get. Is LVM itself a filesystem or is LVM simply a volume manager and you have to subsequently format any volumes you create with mkfs? If it's the later, how does it not break file systems when resizing? What if I'm using something like NTFS. Would I be able to resize an NTFS-formatted volume? I've read through the documentation but I am confused on this point.

---

### Post by ryanhaigh on 2008-10-29
LVM is not a filesystem and you would indeed need to create a filesystem on top of the volume and when you add drives etc you would need to resize the existing filesystem to utilise the new drives. I know that at least ext3 and xfs support this and I am sure there are other filesystems that do also.

As for using NTFS on an LVM volume, I don't think that the LVM volume would be visible to windows as this implementation is a part of the Linux kernel. Now technically I suppose you could create the ntfs filesystem from within Linux but to be honest I don't see the point.

---

### Post by shaggy999 on 2008-10-29
Ok, I was just using NTFS as an example. So if I do a resize I first have to resize the volume and then resize the formatted partition?

---

### Post by ryanhaigh on 2008-10-29
I would imagine that is correct. You would need to use the LVM tools to add your new drive to the volume and then expand the partition on the volume, the links above probably have more accurate and definative information.

---

### Post by GrammatonCleric on 2008-12-05
There's always zfs via fuse....

[https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS)

-GC

---

