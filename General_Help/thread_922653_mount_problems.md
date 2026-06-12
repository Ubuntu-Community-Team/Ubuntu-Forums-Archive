---
title: "mount problems"
date: 2008-09-17
forum: General Help
---

### Post by aaronbp0 on 2008-09-17
I just created a new ntfs partition on my hard drive and can't mount it now! how do I create a mountpoint in ubuntu?

---

### Post by karlr42 on 2008-09-17
```
sudo mount -t ntfs-3g /dev/sda1 /media/disk
```
Replacing sda1 with your NTFS partition and /media/disk with where you want to access the drive from.
If that works, to make it permenant, 
```

sudo gedit /etc/fstab
```
And add something like:
```
/dev/sda1	/media/disk	ntfs	auto,user,exec,rw	0	0
```(those are tabs seperating the entries)
to the end of it. Reboot and check if it's still mounted

---

