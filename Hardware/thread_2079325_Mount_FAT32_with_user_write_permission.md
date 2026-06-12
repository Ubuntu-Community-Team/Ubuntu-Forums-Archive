---
title: "Mount FAT32 with user write permission"
date: 2012-11-01
forum: Hardware
---

### Post by n1ght28 on 2012-11-01
Trying to manually mount a fat32 USB hard drive with write permissions from terminal,

Trying
```
sudo mount -t vfat -o defaults,user,exec,uid=1000,gid=100,umask=000,rw /dev/sda1 /home/shares/public/disk1
```

And I can write to it as root but not as user,

The user has sudo permissions but I need to be ale to write to it without sudo,

Any ideas where I'm going wrong?

---

