---
title: "how do i auto mount usb hard drive"
date: 2008-09-28
forum: Hardware
---

### Post by xmrkite on 2008-09-28
Hello, how do i automount usb hard drives when they are plugged in?

i've edited my fstab to say:

UUID=(here i put the uuid)  /media/drive  xfs  noauto,user  0  0


But when i plug in the usb drive, i get a nice error saying it could not be mounted cause i don't have permission.

The usb drive is not always connected at bootup, so i want to just be able to plug it in like i can with a flash drive, and just have it mount to a predetermined directory automatically.

Any ideas?
-Thanks

---

### Post by olejorgen on 2008-09-29
fstab isn't designed for automounts.

You could run gnome-volume-manager.

From a quick search it seems like autofs, ivman and am-utils is some alternatives.

---

### Post by L815 on 2008-09-29
I'm not sure on the automount issue exactly, but you can bookmark mounts with nautilus :)

---

