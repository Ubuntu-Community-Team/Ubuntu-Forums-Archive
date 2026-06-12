---
title: "Executing a program on an NTFS partition."
date: 2008-07-23
forum: General Help
---

### Post by G Morgan on 2008-07-23
Does anyone know why programs I've built on my NTFS partition (mounted with ntfs-3g) fail to execute giving:

```
make: execvp: ./O3DMTest: Permission denied
make: *** [run] Error 127
```


I've set the uid and umask fields of the fstab entry to 1000 and 022 respectively. The code runs fine on normal partitions. As do the binaries after a simple copy.

I've got some code that needs to be tested on both Windows and Linux and really don't want to copy between my NTFS and Ext3 partitions every time I reboot.

---

### Post by sisco311 on 2008-07-23
add the ***exec*** option to the fstab entry

---

### Post by G Morgan on 2008-07-23
Didn't make a difference. Still won't execute.

The full fstab entry is
/dev/sda1	/media/windows		ntfs-3g		exec,defaults,users,uid=1000,gid=1000,umask=022	0 0

---

