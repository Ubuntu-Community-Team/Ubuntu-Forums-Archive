---
title: "[SOLVED] I changed my external drive's mount point, and now it won't mount at all"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by Frostmourne on 2007-12-29
I am using an external hard drive formatted as ext3. I was tired of it appearing on "/media/disk-1" (I use multiple drives) so I right-clicked on the drive, went to the Drive tab, and typed in "/media/Backups" in the mount point box. When I unplugged the drive and plugged it back in again, now it won't mount at all because I used invalid characters in the mount point box. Is there an easy way to undo this? I searched but it all involves editing fstab and creating directories as root, which shouldn't be necessary since I never used root to edit the mount point in the first place, right?

Thank you for any point in the right direction.

---

### Post by taurus on 2007-12-29
See if you can mount it by hand from a terminal.

Applications -> Accessories -> Terminal
```
sudo mkdir /media/Backups
sudo mount -t ext3 /dev/sdb1 /media/Backups
df -h
```
_Assuming_ your external harddrive is /dev/sdb1.

```
sudo fdisk -l
```

---

### Post by Frostmourne on 2007-12-29
Thanks for the reply. Instead of mounting it by hand, though, I followed the workaround for this bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668)

---

