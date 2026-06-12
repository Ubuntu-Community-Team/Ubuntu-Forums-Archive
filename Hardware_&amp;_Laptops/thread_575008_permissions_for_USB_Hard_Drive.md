---
title: "permissions for USB Hard Drive"
date: 2007-10-13
forum: Hardware &amp; Laptops
---

### Post by phillipss@comcast.net on 2007-10-13
I have an iomega 80 GB usb hard drive that I want to be able to use for backups of my pictures. I used Parted Magic to partition and formatted the drive to ext3. When I boot the system I see the drive as an icon, but I can't transfer pictures to it. The error says that I don't have permission to write to it only root? It is a read only drive at the point, with no data other than a folder(lost&found)?
How can I get the permission changed in order that I can use it as a normal user? 
I am running Ububtu 7.04 RC

---

### Post by aysiu on 2007-10-13
This should help:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by Edaw 0 on 2007-10-14
> **aysiu said:**
> This should help:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

[IMG]http://img.photobucket.com/albums/v505/Edaw010/thumbup.gif[/IMG] Thanks!

---

### Post by vanadium on 2007-10-14
That link is for internal partitions, not for removable partitions. USB drives are automatically mounted with permissions for the current user. Try pluging in the drive after you have logged in. Otherwise, create a directory as root, then chown the directory to yourself as user, then you will always be able to copy your data under that directory, irrespective of who mounted the drive.

---

