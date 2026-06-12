---
title: "Double mounted USB drive"
date: 2010-12-25
forum: Hardware
---

### Post by supercheetah on 2010-12-25
I have a weird problem that's bugging that only just popped up.  My USB flash drive is being mounted twice.  It's not showing up twice on the desktop (like from [this bug]("https://bugs.launchpad.net/gvfs/+bug/251991")), but it is showing up twice in my mounts list:

```

/dev/sdb1 on /media/WinVistaHome__ type xfs (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/WinVistaHome type xfs (rw,nosuid,nodev,uhelper=udisks)
```

Another thing that happens is that the first mount does not delete the mount directory once it's been unmounted, but the second one does properly.  And if I don't delete the first directory every time after unmounting, I get this after a while in /media:

```

drwx------ 2 root root 4.0K 2010-12-25 05:25 WinVistaHome_
drwx------ 2 root root 4.0K 2010-12-25 05:25 WinVistaHome__
drwx------ 2 root root 4.0K 2010-12-25 05:34 WinVistaHome___
drwx------ 2 root root 4.0K 2010-12-25 05:35 WinVistaHome____

```

Anyone know what's going on here?

---

### Post by Fafler on 2010-12-25
I don't think it's being mounted more than once each time you connect the drive, it's just not being unmounted.

Try unmounting them manually with:

```
 find /media -name 'WinVistaHome*' -exec sudo umount {} \;
```As to why it's not being unmounted by the automounter, i don't really know. Maybe some program is using it. Look at the tools fuser and lsof to investigate.

Also, if the script refuses to work, add -l as a option to umount to force it. It might cause the program trying to access the drive at the old mountpoints to crash.

---

### Post by 3togo on 2011-03-11
try uninstall hal which is obsolete and is the cause of double mount 

```
sudo apt-get remove hal
```

---

