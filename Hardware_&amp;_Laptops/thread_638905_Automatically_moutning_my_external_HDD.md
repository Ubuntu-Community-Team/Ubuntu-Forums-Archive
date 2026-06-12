---
title: "Automatically moutning my external HDD"
date: 2007-12-12
forum: Hardware &amp; Laptops
---

### Post by shanedj on 2007-12-12
I have this that works to mount my drive
```
sudo mount -t ntfs-3g /dev/sdb1 /mnt -o force
```

how do I translate this to populate the /etc/fstab file

thanks

---

### Post by dabl on 2007-12-12
Here's an example -- it is an 8GB USB thumb drive formerly known as /dev/sde1, formatted NTFS, and using the "mount by UUID" approach:

```
# Entry for /dev/sde1 :
UUID=A8FC3435FC33FC5E /media/NTFSTICK ntfs-3g nouser,defaults,atime,exec,force 0 2
```

The reason I like "mount by UUID" is that the /dev/sdx number of a USB device is dynamically assigned, and can change from one bootup to the next.  The UUID stays the same, at least until your reformat it change filesystem type or something drastic like that.

Find the UUID of that drive by entering the command ```
blkid
```

:guitar:

---

