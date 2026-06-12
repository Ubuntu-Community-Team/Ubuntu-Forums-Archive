---
title: "CLI command to list all devices?"
date: 2008-09-01
forum: General Help
---

### Post by harryliddic on 2008-09-01
Is there a CLI command that lists all devices and there mount points?

---

### Post by ~LoKe on 2008-09-02
```
mount
```
?

---

### Post by harryliddic on 2008-09-02
**mount** lists my disk partitions but not my floppy, cd-rom, and dvd

---

### Post by Oldsoldier2003 on 2008-09-02
> **harryliddic said:**
> Is there a CLI command that lists all devices and there mount points?

For what purpose are you needing this information? With more information we could steer you to exactly what you want for your purpose. ```
ls -alh /dev/disk/by-path
``` will give you all your partitions...

---

### Post by harryliddic on 2008-09-02
I want to made sure my dvd-rw drive is mounted  /dev/dvd because Kino writes to a device that name in one of its export variations. I also have been hanging up when I use qdvdauthor and thought that mount point might help. This assumes that I can change the mount point with **mount /dev/oldname  /dev/dvd**

---

### Post by harryliddic on 2008-09-02
searching through some old unix books I found **cat /etc/fstab** and it produced this read out for the devices 

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

the /dev/scd1 is my dvd drive but it has the same parameters as my cd drive
is this right?

---

