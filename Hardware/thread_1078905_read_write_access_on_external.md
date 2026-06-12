---
title: "read write access on external"
date: 2009-02-23
forum: Hardware
---

### Post by Forged on 2009-02-23
Im using debian lenny with gnome, and I don't have rw access to my external usb hd.

It auto mounts but gives me an error everytime I try to create a folder, or copy a file to it. 

I tried to chmod, but that didn't work, and editing the fstab file didn't work either, what should I do?

---

### Post by whoop on 2009-02-23
What file system is the hd using?

---

### Post by Forged on 2009-02-23
fat32

---

### Post by drhiii on 2009-02-24
Exactly same thing here.  vfat on a USB device.  Three in fact.  Working perfectly in 8.04.  Moment I upgraded to 8.10, it failed.  Filesystem states it is read-only.  No matter what I do, I cannot change perms, unmount and remount, nothing works.  The device(s) have not changed.  I even reinstalled into a fresh 8.10 and same thing.  Cannot write to the USB external devices.  

Have rooted around quite a bit for a week and have not found a solution.  It is important to state that it was working fine in 8.04, but 8.10 appears to have changed something.

Ideas anyone?

---

