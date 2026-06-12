---
title: "How to safely remove the external hard disk"
date: 2009-01-23
forum: Hardware
---

### Post by linuxmascot on 2009-01-23
Plzz help me how to remove hard disk safely from ubuntu ...

just unmounting the drive is not enough right?

---

### Post by Yashiro on 2009-01-23
It is enough, yes.

---

### Post by amac777 on 2009-01-23
> **linuxmascot said:**
> Plzz help me how to remove hard disk safely from ubuntu ...

just unmounting the drive is not enough right?

You need to unmount it before you unplug it. Something like this:

```
sudo umount /media/disk
```

where /media/disk can be changed to whatever mount point you used for the disk.

if you don't like the command line, you can right-click on the icon for the disk on your desktop and select something similar to "Unmount" or "Eject".

---

