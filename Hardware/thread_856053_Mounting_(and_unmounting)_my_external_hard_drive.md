---
title: "Mounting (and unmounting) my external hard drive"
date: 2008-07-11
forum: Hardware
---

### Post by Johnny K on 2008-07-11
I have an external hard drive which contains two partitions - one is ext3 and one is FAT32. Each partition mounts automatically at boot and I am able to read/write to the partitions without any special effort. However, I am unable to unmount the partitions normally. I can only unmount them with sudo umount.

I have some understanding of fstab, but obviously not enough. Below are my entries for the partitions:
```

/dev/sdb1   /media/external_main    ext3    auto,user,rw,errors=remount-ro                    0   1
/dev/sdb2   /media/external_fat32   vfat    rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000   0   0
```

I can't seem to understand what is causing the problem. Could it be that I am not using UUIDs, did I do something wrong in the options section, or is it something else entirely?

Thanks in advance!

---

### Post by vanadium on 2008-07-11
An external hard drive should not be included in /etc/fstab. Ubuntu automatically mounts an external drive when it is being plugged in. The idea behind this is that an external drive is not necessarily there when the system boots. That said, you can still use fstab if you wish.

In response to your question, you should use the option "users" instead of "user" to allow  allow any user to unmount.

If you use "user", then only the user who mounted the device can unmount it. In your current case, root mounted the drive, thus only root can unmount. After unmounting the partitions as root, you probably will be able to remount and unmount as normal user.

---

### Post by Johnny K on 2008-07-11
Ahh great. thank you for all the great information.

If I do not include the drives in fstab, though, will they still be mounted at boot?

---

### Post by vanadium on 2008-07-11
External USB drives: yes.

---

