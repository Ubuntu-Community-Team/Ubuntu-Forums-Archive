---
title: "Western Digital My Book NTFS drive switches to ro"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by KaiserMonkey on 2007-11-06
Hi,

I've been an Ubuntu user since May. I recently installed Gutsy (a clean install, since my upgrade didn't work right) and have been getting a problem with my 250gb Western Digital My Book NTFS USB drive. It mounts as rw, but it won't let me move, delete, or change files.

Following the instructions from a previous thread, I changed a couple things from gconf - namely the "uid" and "umask" lines - and now running "mount" in a terminal gives me:

```
/dev/sdc1 on /media/My Book type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
```

Despite the rw in the mount output, I am still unable to write to the drive.

Any suggestions?

---

### Post by ddrichardson on 2007-11-06
If its an NTFS drive, why is it specified as VFAT in the fstab line?

---

