---
title: "[SOLVED] Can't get rid of virtual drives (mounted ISO's)"
date: 2008-10-05
forum: General Help
---

### Post by adlin5000 on 2008-10-05
I tried to mount an ISO with Acetone2iso and now i cant get rid of the drives. The drive failed to mount (could not access it) but it still created a icon on the desktop and in the "Places" menu. When I try to unmount or delete the drive I get this:

```
Unable to unmount 1
umount: /home/adlin5000/.local/share/Trash/files/virtual-drives/1 is not mounted (according to mtab)

```

Any suggestions?

---

### Post by nikgare on 2008-10-05
what's the output of **df -u** ?

---

### Post by CrusaderAD on 2008-10-05
Check out your fstab file... sudo vi /etc/fstab if it lists the drive it may still try to access it.

---

### Post by mssever on 2008-10-05
Actually, the best way to find details of what's mounted is to type ```
mount
```You can then unmount it as it's listed there, using sudo if necessary.

---

### Post by adlin5000 on 2008-10-06
Thanks for the input. 

Apparently I found a way to fix it. I had to uninstall Acetone2iso, move the "Virtual drives" folder to the trash(it would not delete yet), reboot a few times, reinstall Acetone2iso, mount a different image and unmount it, reboot a few more times and then they went away finally.

Not sure what parts of that actually helped, but it worked.

---

### Post by dokc on 2008-12-06
I had the same problem and solved it without uninstalling Acetoneiso2.

check the fuseiso mounted folders
```
mount
```

you will get a list of mounted devices and between them something like:

```
fuseiso on /home/test/virtual-drives/dvd type fuse.fuseiso (rw,nosuid,nodev,user=test)
```

unmount device using:

```
fusermount -u /home/test/virtual-drives/dvd
```

---

