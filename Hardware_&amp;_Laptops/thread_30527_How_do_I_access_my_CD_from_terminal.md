---
title: "How do I access my CD from terminal?"
date: 2005-04-29
forum: Hardware &amp; Laptops
---

### Post by Zensunni on 2005-04-29
This is probably the dumbest question ever, but I don't know how to get into my CDrom. I can't use my GUI because my VGA card doesn't have a driver, so I'm using the terminal. I beleive you'd just go into /cdrom but every time i go to it, there's no files there. Do I have to type a command to refresh the folder? I'm logged in as root and i'm in "/". Do I have to mount it first? If so, do I use "cdfs" as the file system mount?

BTW, my VGA card driver is on the CD, which is why i'm trying to get at it....

---

### Post by heimo on 2005-04-29
If you have your cdrom device with mountpoint and filesystem defined in /etc/fstab, it can be as simple as using *mount /cdrom *or *mount [mountpoint]* in pseudo.

If it's not in fstab, you can *mount /dev/hdc /cdrom *(for example, if device is hdc, master on second ide channel). Sometimes you need to define filesystem with flag -t (see man mount and man fstab for details).

---

### Post by Zensunni on 2005-04-29
Thanks so much! I feel so retarded....but now I feel even more retarded, because I don't know how to open this ".run" file.....

---

### Post by Zensunni on 2005-04-29
wiat, don't answer that - i found it ....just typed sh

---

