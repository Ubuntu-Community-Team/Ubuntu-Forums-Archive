---
title: "Grsync and permissions"
date: 2008-11-04
forum: General Help
---

### Post by tea for one on 2008-11-04
Good evening

I have found Grsync to be reasonable suitable for back up purposes but there is an issue that seems inexplicable.

I have made a partition with ntfs file format on an external HDD and Grsync works perfectly, both back up and restore. (without sudo or sudo bash)

I then changed the format to ext 3 and I receive a "permission denied" warning and Grsync fails.

It seems peculiar that it fails if the user chooses a native Linux format.

I suspect that I have to invoke sudo somewhere but the application does not need superuser privileges to read and write to an ntfs partition?


Thanks in advance

---

### Post by fatphilthethird on 2008-11-05
Try running the programme as sudo:

```
gksudo grsync
```

Fat

---

### Post by geirha on 2008-11-05
ext3 filesystems are only writeable to root by default. Just change the ownership of the filesystem to yourself. If it's mounted at /media/disk
```
sudo chown $USER:$USER /media/disk
``` and you should have full access to create files and directories inside /media/disk.

---

### Post by tea for one on 2008-11-05
Thanks for the replies, I did suspect that there would be issues of file ownership to overcome.

However, it is widely known that certain operations require superuser powers in Ubuntu but I was surprised to find that backing up and restoring files could sometimes be accomplished without a password.

To recap:-

Backup and restore to (or from) a destination formatted ntfs = no password
Backup and restore to (or from) a destination formatted ext3 = password

It does appear that there is a little aperture in the Ubuntu security system, and I qualify this comment by restating that I was using Grsync.

Perhaps, I should use alternative backup software to close the trap door?

---

### Post by geirha on 2008-11-05
Linux is currently unable to apply permissions to files and directories on NTFS filesystems, so instead you set the same permissions and ownership 
for all files and folders on that filesystem during mounting. If you have an external drive with an NTFS or FAT partition that you connect with USB, gnome will mount it and set the permissions and ownership to the user currently logged in, giving that user full access to the drive, meaning no sudo necessary.

On ext3 however, you can set different permissions and ownerships on all files, giving you the ability to make certain files and folders writeable to some, and only readable to others, or make files and folders completely inaccessible to everyone but one user, etc ... The root user of course, has access to everything no matter what. But the point is, you need to set up these permissions manually on ext3 filesystems, to fit your needs. And by default, a freshly formatted ext3 is readable to all, but only writeable to root.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

