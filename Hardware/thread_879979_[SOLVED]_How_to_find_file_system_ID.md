---
title: "[SOLVED] How to find file system ID"
date: 2008-08-04
forum: Hardware
---

### Post by Jordanwb on 2008-08-04
In /etc/fstab you can have Linux mount a partition by /dev/sd[] or by a File System ID. How do I find out what the ID is for a given file system.

---

### Post by sisco311 on 2008-08-04
```
sudo blkid
```or
```
sudo blkid /dev/sd***XY***
```or
```
sudo vol_id -u /dev/sd***XY***
```

---

### Post by krippa on 2009-07-28
You can also use simple ls commands to get fs info that don't require you to execute them as super user:

#fs id
ls -l /dev/disk/by-uuid/     

#some other id that is especially useful when a fs doesnt have uuid (which was the case for a packard bell mp3-player I have).
ls -l /dev/disk/by-id/       


source: [http://www.linuxforums.org/forum/misc/20903-uuid-2.html]("http://www.linuxforums.org/forum/misc/20903-uuid-2.html")

---

