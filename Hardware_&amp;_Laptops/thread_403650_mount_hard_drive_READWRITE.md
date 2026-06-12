---
title: "mount hard drive READ/WRITE"
date: 2007-04-07
forum: Hardware &amp; Laptops
---

### Post by brad1150 on 2007-04-07
it seems that nobody knows how to mount a hard drive with read/wdoes anybody know hwo to do this?

---

### Post by goodfella on 2007-04-07
In your /etc/fstab file you should have the following:
```
/dev/sda2       /media/media     ext3    defaults        0       2
```

/dev/sda2 is the device I wish to mount
/media/media is where I want to mount the drive to.
defaults mounts the drive read/write

consult the manpage for mount by typing ```
man mount
``` in a terminal.

to mount a drive read/write from the terminal just type:
```
sudo mount -t ext3 -O defaults /dev/hdb2 ubuntu-6-01/
```
ext3 is the file system type
-O defaults sets the options; the default option is read/write
/dev/hdb2 is the device I wish to mount
ubuntu-6-01 is where I want to mount the drive to; Note: ubuntu-6-01 is in the directory I run mount in for this example.

---

### Post by brad1150 on 2007-04-07
It still mounted as read only with root permissions. It said cannot change file permissions: read only filesystem

---

### Post by Pyro_Killer on 2007-04-10
write:
sudo chown username /where/your/harddrive/is

---

### Post by amohanty on 2007-04-10
> sudo chown username /where/your/harddrive/is

Thats a bit of overkill that may come back to bite you in the behind :) especially on a multiuser system.

I would suggest instead of **default** in the abovementioned fstab entry, try using **auto,user,rw**

This will automatically mount the drive, in read/write mode and will also allow authorised users to mount it if needed.

HTH
AM

---

### Post by jack1254 on 2007-04-10
Are you talking about an ext3 (default "linux" filesystem), or something else (Windows NTFS?)?

If you are talking about NTFS, look into something called *ntfs-3g*. The NTFS drivers you are using probably are not setup for read/write.

Other filesystems may have other requirements in terms of drivers, I don't really know.

---

### Post by pjrodz on 2007-04-18
> **amohanty said:**
> Thats a bit of overkill that may come back to bite you in the behind :) especially on a multiuser system.

I would suggest instead of **default** in the abovementioned fstab entry, try using **auto,user,rw**

This will automatically mount the drive, in read/write mode and will also allow authorised users to mount it if needed.

HTH
AM

i tried this but it still mounted as read only with root permissions. It said cannot change file permissions: read only filesystem. pls help me. thanks! i'm mounting a ext3 (default "linux" filesystem) filesystem.

---

### Post by devnulljp on 2007-04-19
mount -t ext3 -o rw /dev/whatever /some/mount/point

---

### Post by pjrodz on 2007-04-19
> **devnulljp said:**
> mount -t ext3 -o rw /dev/whatever /some/mount/point

i need something i could put into the fstab so that it my linux partition will automatically be mounted in read/write mode. thanks again!

---

### Post by pjrodz on 2007-04-19
> **pjrodz said:**
> i need something i could put into the fstab so that it my linux partition will automatically be mounted in read/write mode. thanks again!

anyone? thanks! :)

---

### Post by david_kt on 2007-04-28
> **pjrodz said:**
> anyone? thanks! :)

Try to run below code in terminal:

```
sudo chmod 777 /mnt/your_mount_point
```

DK

---

