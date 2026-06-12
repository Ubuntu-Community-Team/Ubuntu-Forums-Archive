---
title: "Always mounts drive as read-only"
date: 2008-11-18
forum: General Help
---

### Post by potator on 2008-11-18
So I recently partitioned my hard drive for a dual boot system with a shared file area.  However, no matter what I do, the drive always mounts as read only.

I have already tried:
making sure rw was an fstab option -seems to do nothing
chown -operation not allowed
chmod -looks like it has succeeded, but reverts files to read-only (even with sudo)

The main reason I am trying to mount this though, is because i am trying to make links to the music/pictures/videos/documents folders on the shared partition in my home folder, but it wont allow the links if i let LinuxMint autodetect the partition

---

### Post by drs305 on 2008-11-18
> **potator said:**
> So I recently partitioned my hard drive for a dual boot system with a shared file area.  However, no matter what I do, the drive always mounts as read only.

Is this an NTFS partition?

> 
I have already tried:
making sure rw was an fstab option -seems to do nothing

Install ntfs-config if Linux Mint has it. It will allow you to configure your NTFS partitions as read/write. Once installed, run ntfs-config and it will create a /media mountpoint (ex: /media/myfiles) or you can enter a mount point that already exists and will then enable RW capability.

> 
chown -operation not allowed

Did you use "sudo chown" - if the file or folder is owned by root you must include "sudo" to change ownership. That being said, if the partition is an NTFS partition, ownership is set at the time of mounting and cannot be changed.

If you already have a line in fstab for the partition and post it here we can probably help you sort this out.

---

### Post by potator on 2008-11-18
It is a FAT32 filesystem.  I tried all the commands as root.

---

