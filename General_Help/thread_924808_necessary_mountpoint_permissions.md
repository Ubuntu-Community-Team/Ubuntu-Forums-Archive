---
title: "necessary mountpoint permissions"
date: 2008-09-19
forum: General Help
---

### Post by Meson on 2008-09-19
What are the requirements for a user to mount something in the fstab?  rx permissions on the directory?

Here's what is troubling me.  I have the following lines in my fstab.
```

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

//windows-machine/share	/media/windows-machine/share cifs noauto,user,file_mode=0600,dir_mode=0700,credentials=credfile 0 0

```
So, cds and that windows share should both be able to be mounted by ordinary users.

Here's the listing of each mountpoint and the mount commands:
```

drwxr-xr-x 2 root root 4096 2008-09-14 22:46 cdrom0
drwxr-xr-x 2 root root 4096 2008-09-18 14:39 share

-rwsr-xr-x 1 root root 81368 2008-04-29 07:57 /bin/mount
-rwsr-xr-x 1 root root 23340 2008-09-10 14:55 /sbin/mount.cifs

```

So everything should behave exactly the same.  However, the cdrom mounts just fine and the windows share fails with this:
```

mount error: permission denied or not superuser and mount.cifs not installed SUID

```

(Note: if I change ownership on the mountpoint for the windows share it all works fine, but I don't see why there should be a difference between this two devices.)

---

