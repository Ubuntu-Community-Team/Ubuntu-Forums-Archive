---
title: "NTFS and Ubuntu"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by selmore on 2008-01-18
Hi, i'm bit of a newb to Ubuntu here.

I have Ubuntu 7.10, and I need to re-install Windows, the problem is i need to keep a backup of the drive. I try accessing it, but it says it cannot mount the drive. Included is the error I get. Please help.

---

### Post by Borbus on 2008-01-18
You have to force mount it because windows didn't cleanly shut down. Open a terminal and type ```
sudo mount -t ntfs-3g /dev/sda1 /media/250GB HDD -o force
```

---

