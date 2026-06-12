---
title: "NTFS USB not automounting"
date: 2008-11-26
forum: General Help
---

### Post by grkuntzmd on 2008-11-26
I am running Intrepid. I have a 200GB NTFS USB drive permanently connected. When I reboot, my ext3 external drive (250GB USB) automounts, but the NTFS one does not.

Here is my /etc/fstab line:

UUID=A004C0AC04C0872E /media/Medium_disk ntfs defaults,nls=utf8,relatime,errors=remount-ro,user,umask=000 0 0

I confirmed that the UUID is correct.

I am running Gnome.

Any ideas?

---

### Post by Titan8990 on 2008-11-26
Does it work properly if you give the command to mount that drive without a given mount point?

Example assuming drive /dev/sdb1:


sudo mount /dev/sdb1

---

### Post by grkuntzmd on 2008-12-05
I don't know. I reformatter that drive and a new one that I connected (also with NTFS) seems to automount fine.

Thanks.

---

### Post by taurus on 2008-12-05
Is everything working now or that USB drive still won't mount upon boot?

```
sudo fdisk -l
sudo blkid
df -h
```

---

### Post by grkuntzmd on 2008-12-05
Seems to be working well now.

---

