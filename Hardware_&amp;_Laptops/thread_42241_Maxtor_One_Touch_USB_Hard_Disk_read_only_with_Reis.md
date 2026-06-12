---
title: "Maxtor One Touch USB Hard Disk read only with ReiserFS"
date: 2005-06-16
forum: Hardware &amp; Laptops
---

### Post by jasonmallison on 2005-06-16
Hi all,

I have a 200GB Maxtor USB Hard Disk formatted with ReiserFS that mount automatically without any problem, using gnome-volume-manager etc. However it always mount read only for normal users, and says it is owned by root. However when I plug my usb memory stick in it mounts read-write and is owned by myself. I have tried writing udev.rules but have not had any luck. Has anyone else had any issue like this? Anyone gotten it resolved? Like I said Hoary mounts it no problem and I can copy from it, I just cannot write anything to it.

Thanks in advance for any help...

---

### Post by alastair on 2005-06-16
[QUOTE=jasonmallison]Hi all,

I have a 200GB Maxtor USB Hard Disk formatted with ReiserFS that mount automatically without any problem, using gnome-volume-manager etc. However it always mount read only for normal users, and says it is owned by root. However when I plug my usb memory stick in it mounts read-write and is owned by myself. I have tried writing udev.rules but have not had any luck. Has anyone else had any issue like this? Anyone gotten it resolved? Like I said Hoary mounts it no problem and I can copy from it, I just cannot write anything to it.

Thanks in advance for any help...[/QUOTE]
 Your usbstick might have a different filesystem (FAT?) and so have different mount options. I've never used Reiser - but check :

a) the /etc/fstab file
b) manual page (man fstab ?)

You can often set options like uid, user, gid etc.

---

### Post by jasonmallison on 2005-06-17
But I don't have to put an entry in my fstab for the usb sticks, so why should I have to put on in there for the hard disk? Shouldn't it just work, you would think if the memory stick works the hard disk should too. You would think this would be file system independent, with exception to ntfs... Anyone else have any thoughts?

---

### Post by kiddo on 2005-09-18
same problem! FAT is getting me crazy, and I have NOT been able to automount any other filesystem yet! ;___; are we the only ones crazy enough to use reiserFS on a USB hard drive?

---

