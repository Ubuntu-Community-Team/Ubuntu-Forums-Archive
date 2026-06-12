---
title: "Usb pen problems."
date: 2006-02-06
forum: Hardware &amp; Laptops
---

### Post by Nevermore on 2006-02-06
On an ubuntu machine there are some problems mounting the usb pen, the usb pen lights on and is recognized by the system, but is impossible to see what is inside as well as copying files into.
The system gives this error:
wrong fs type, bad superblock, or bad option.
and the pen is not working.
i tried to enter from  disk manager but it got stuck and didn't even load.
is it needed to do some operation before mounting the pen or it should be working "out of the box"?
i tried to restart also hotplug but nothing changed.
Thanks all.

PS the thumbdisk was formatted in fat32 under winxp.

---

### Post by joey111 on 2006-02-06
did mounting worg in /etc/fstab?
u could try to get a line like
/dev/sda1      /media/usb1     vfat user,noauto,rw,exec,umask=000 0 0
there, then it would mount it there everytime u hotplug the stick;
if u dont want it use the hashmark and comment it out;

---

