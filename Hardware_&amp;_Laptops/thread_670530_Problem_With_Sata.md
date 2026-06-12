---
title: "Problem With Sata"
date: 2008-01-17
forum: Hardware &amp; Laptops
---

### Post by donthem on 2008-01-17
Hello, I recently installed a new Sata Controller to an old Sony Vaio running Ubuntu Server.  While the drive shows up correctly, when i reboot it changes its boot device identifier.  Somtimes it is /dev/sda and sometimes its /dev/sdd (the last drive detected).  Is there a way to fix this?

Thank you

---

### Post by Yellow Pasque on 2008-01-17
Not sure how to remedy that directly, but you can minimize its effect by mounting devices with the UUID in your /etc/fstab file, . To get the UUID:
```
cd /dev/disk/by-uuid/; ls -l
```

Example:
```
lrwxrwxrwx 1 root root 10 2008-01-16 12:44 7a119114-4fd7-4ee0-922f-a7d03a5b4b3e -> ../../sda1
```
so the fstab line looks like
```
UUID=7a119114-4fd7-4ee0-922f-a7d03a5b4b3e   /    ext3    defaults,errors=remount-ro   0    1
```

---

### Post by donthem on 2008-01-30
i see what your getting at.  I was using the drive as part of a mdadm raid, and it turns out that the raid drive loads regardless of the sata harddrive identifier.  So even if it loads at sda, the md0 still gets mounted.  I thank you for your reply, and i will try this if i ever need to mount the drive when it is not part of a raid.

-thank you

---

