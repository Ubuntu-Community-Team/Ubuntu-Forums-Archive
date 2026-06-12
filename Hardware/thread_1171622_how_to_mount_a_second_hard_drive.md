---
title: "how to mount a second hard drive?"
date: 2009-05-27
forum: Hardware
---

### Post by raptor222 on 2009-05-27
Hi,
I installed an second hard drive on my Ubuntu machine and formatted it as EXT3 but the problem now is that it does not shows anywhere and i don't know how to mount it properly (so it will appear on the desktop and/or on in the computer)

---

### Post by taurus on 2009-05-27
_Assuming_ it is /dev/sdb1, you can edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it to have it mounted automatically each time you boot Ubuntu.

```
/dev/sdb1   /media/sdb1   ext3   defaults   0   2
```
Save it.  Then, create the new mount point, /media/sdb1, and mount it.

```
sudo mkdir /dev/sdb1
sudo mount -a
df -h
```

---

### Post by raptor222 on 2009-05-27
It worked, but I wanted to mount the new drive as an drive (and have the system recognize it as such).

---

### Post by taurus on 2009-05-27
What do you mean you want to mount it as a drive?  Everything in Linux/Unix is either a file or a directory.  You access your second harddrive by accessing the mount point, not the drive itself.

---

### Post by raptor222 on 2009-05-27
I simply want it to show like the file system drive (I know it is possible with network shares)

---

