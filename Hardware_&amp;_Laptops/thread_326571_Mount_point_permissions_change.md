---
title: "Mount point permissions change"
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by ka1ssr on 2006-12-27
Hello!

I am running Edgy and I am trying to recover some documents from a hard drive with a borked Windows XP OS.  I have installed the hard drive in the PC and made a mount point in /media/hdb1.Here is what the permissions look like:
drwxr-xr-x 2 root root 4096 2006-12-27 19:45 hdb1.

I added the drive to my fstab file: /dev/hdb1 /media/hdb1 ntfs rw,users 0 1 and I mounted it using mount /dev/hdb1.  The mount command completes with no errors and when I issue the df command I can see the drive.  But when I go to the mount point, I discover that the permissions have changed to:
dr-x------ 2 root root 4096 2006-12-27 19:45 hdb1

...and I can't access hdb1.

Any ideas why this is happening?

Feel free to issue a dope slap if this is something painfully obvious.

Many thanks for your help!

Bill

---

### Post by kidders on 2006-12-28
Hi there,

> Feel free to issue a dope slap if this is something painfully obvious.Lol it's only obvious if you know the answer!!

You might not have thought about this before, but just like any other directory in a filesystem, its root also has permissions assigned to it. In fact, Gentoo made a booboo with root directory permissions not so long ago. When you mount a filesystem, the mount point is usually assigned the permissions of the filesystem's root.

Now, since the HD you're working with has Windoze on it, it's probably got no ownership/permissions support, so it's actually very encouraging to see that your Ubuntu box has been as conservative as this with the permissions assigned to the mount. :-)

Some things to notice:

[LIST]
[*]Linux won't let you write to NTFS out of the box, so that's why the "w"s are missing.
[*]You can use the "umask" mount option to set your own file/directory permissions for the mount.
[*]You can use the "uid" and "gid" mount options to control who owns the mounted files.
[/LIST]

---

### Post by ka1ssr on 2006-12-28
Many thanks!

I mounted the drive with the umask, guid and uid parameters and now I can grab stuff off the drive.

Many thanks for your help.

Bill

---

### Post by kidders on 2006-12-28
No problem :-)

---

