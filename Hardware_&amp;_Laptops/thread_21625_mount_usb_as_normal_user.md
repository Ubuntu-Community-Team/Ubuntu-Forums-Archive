---
title: "mount usb as normal user"
date: 2005-03-23
forum: Hardware &amp; Laptops
---

### Post by civ247 on 2005-03-23
hi ubuntu is a bit unreliable when detecting my usb pen drive, so ive resorted to mounting it from bash. The problem is that i can only moutn it as root user meaning that when i  go back to gnome it wont let me drag & drop files because im logged in as a normal user. 

How can ichange it so i can mount drives as a normal user or is there any other solution?

Thanks

---

### Post by ola on 2005-03-24
Have you put the USB stick in /etc/fstab so it takes care of the mounting?
If so, you could try to add a user in the line that takes care of the stick.

/dev/sda1       /mnt/usbstick           auto    defaults,user        0       0

Im not totaly shure about, but you could try..

---

### Post by alastair on 2005-03-24
As well as the "user" option, you might want to look at using the "uid" and "gid" options. See :

man mount

(probably options for type "vfat")

---

