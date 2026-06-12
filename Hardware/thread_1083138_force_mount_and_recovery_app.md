---
title: "force mount and recovery app"
date: 2009-02-28
forum: Hardware
---

### Post by pdcox on 2009-02-28
i want to know if there is any hard disk recovery aplication avaible for ubuntu. i have one external hard disk that i am not being able to mount.
how do i force a mount.

---

### Post by pdcox on 2009-02-28
bump

---

### Post by taurus on 2009-02-28
Is it ntfs filesystem?

You would do something like

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
```
_Assuming_ /dev/sdb1 is the partition/drive that you want to force mount it.  Also, you can use ntfsfix to fix the not "safely remove hardware" message if that is the problem that prevents you from mounting it without using the force option.

```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
sudo /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```

---

### Post by pdcox on 2009-02-28
thanks alot, i was able to mount but i have another hd that has a problem do u know any recovery program so i can get my files back

---

### Post by taurus on 2009-02-28
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by pdcox on 2009-02-28
thanks man

---

