---
title: "Second Hard Drive Write Permissions"
date: 2008-03-10
forum: Hardware &amp; Laptops
---

### Post by johnnybgood115 on 2008-03-10
There are a lot of threads on this topic so please don't burn me cause I've made another.  I've read through all of them and can't seem to figure out what's going on with my system. 

I have to hard drives on my laptop. The first is my filesystem and the second is a FAT32 60GB hard drive found /media/sdb1

I cannot write or change files (delete files) on this second drive.  My machine tells me its a read only drive. 

I have tried both.....

```
sudo chmod 777 /media/sdb1
```
and...
```
sudo chown 777 /media/sdb1
```

Both to no avail.  Are there any other suggestions? 

Thanks in advance...

---

### Post by taurus on 2008-03-10
Try

```
sudo umount /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
ls -la /media
```

p.s.  Do you automount your second harddrive, /dev/sdb1, from /etc/fstab?

```
cat /etc/fstab
```

---

