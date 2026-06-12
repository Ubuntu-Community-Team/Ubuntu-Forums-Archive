---
title: "Mount virtual disk files(.disk)"
date: 2010-07-03
forum: Hardware
---

### Post by Joachricar on 2010-07-03
Hey!

The first time i installed ubuntu, i installed it with wubi.
It made the virtual disks root.disk and swap.disk.

So after using it a bit i found out that i liked ubuntu and wanted a bit more space for it(i only gave wubi 15gb =/), so i made a new partition on a disk and installed ubuntu on that one. The problem is that after i installed it this time, i cant access the old one. I only get an error on the win7 loader, where it says something bout chkdsk and so on. I have some files on the old ubuntu that i want to get back.

Ive googled around for a way to mount the .disk file, but i dont find anything useful. Anyone have a way to access it?

---

### Post by Joachricar on 2010-07-03
Typical. After making a new thread i found a solution.

```

sudo mount -t ntfs /dev/sdb1 /media/<name here>
sudo mkdir /media/root.disk
sudo mount -o loop /media/<name here>/ubuntu/disks/root.disk /media/root.disk

```

a more detalied version here:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)

---

