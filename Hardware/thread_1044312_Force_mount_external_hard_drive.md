---
title: "Force mount external hard drive"
date: 2009-01-19
forum: Hardware
---

### Post by boburob on 2009-01-19
Whats the command to force mount a phillips external hard drive, I have done it before but now its just confusing me....lol

Thanks for any help:)

---

### Post by taurus on 2009-01-19
I assume you mean force mount an ntfs drive.  Instead of force mounting it, why not fix the problem.  Connect it to a windows machine and use the safely remove hardware option to unmount it first before you unplug it.  Otherwise, use ntfsfix in Ubuntu to fix it.

```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
```
Assuming /dev/sdb1 is your external ntfs drive.

But if you still want to force it, then run

```
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
```
Assuming you already have the mount point /media/sdb1.

---

### Post by boburob on 2009-01-19
Thankyou,

and i dont have a windows machine to connect to, the hard drive came with a dirty flag:/ This is the first time connecting it

---

