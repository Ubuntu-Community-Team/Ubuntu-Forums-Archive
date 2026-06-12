---
title: "Unable to write to locally mounted drive"
date: 2010-01-18
forum: Hardware
---

### Post by lsutiger on 2010-01-18
I have a second hard drive in my case that is formated as ext4.
The line I have in my fstab for the drive is here:
```
UUID="4cf30274-7261-4837-86fe-b5fd300a2cee" /mnt/disk2    ext4    users,noatime,auto,rw,nodev,exec,nosuid 0 0
```
when I run sudo umount -a, I do not get any errors. To test I tried to copy a file to this drive.
This is the result:
```
cp ~/tm.txt /mnt/disk2/
cp: cannot create regular file `/mnt/disk2/tm.txt': Permission denied

```
from ls I notice full permissions are not available:
```
drwxr-xr-x 9 root root  4096 2010-01-15 16:21 ..
drwxr-xr-x 3 root root  4096 2010-01-15 16:07 .

```
Shouldn't the rw in the fstab string make it available for writing?
I do have several other network shares mounted under the same directory /mnt.
Now, I can chmod 777 that directory, but will that stick through a reboot?

---

