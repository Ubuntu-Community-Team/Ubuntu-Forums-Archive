---
title: "Mounted Disk permissions"
date: 2008-10-07
forum: General Help
---

### Post by RyanfromtheShire on 2008-10-07
So I have my PSP plugged into, via USB and it's mounted. It says it's "read-only", so I type this in:

```

ryan@ryan:~$ ls -l /media
total 20
lrwxrwxrwx  1 root root    6 2008-07-11 02:22 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2008-07-11 02:22 cdrom0
drwxr-xr-x  2 root root 4096 2008-07-11 02:22 cdrom1
drwxr-xr-x  2 root root 4096 2008-07-11 09:11 datapartition
drwxrwxrwx  6 root root 4096 2008-10-06 20:19 disk
drwx------ 11 ryan root 4096 1969-12-31 18:00 disk-1
ryan@ryan:~$ chmod 777 /media/disk-1
chmod: changing permissions of `/media/disk-1': Read-only file system

```

It won't change the permissions. I basically need to know what I'm doing wrong.

---

### Post by iaculallad on 2008-10-07
Remember that Linux folder/file permission cannot be applied to NTFS formatted drives. 
The drivers (NTFS-3G) for example only permits you to perform read and write to NTFS drives.

---

### Post by RyanfromtheShire on 2008-10-07
> **iaculallad said:**
> Remember that Linux folder/file permission cannot be applied to NTFS formatted drives. 
The drivers (NTFS-3G) for example only permits you to perform read and write to NTFS drives.

Dur! haha thanks!

---

