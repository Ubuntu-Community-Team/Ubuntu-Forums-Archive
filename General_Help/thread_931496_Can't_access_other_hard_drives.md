---
title: "Can't access other hard drives"
date: 2008-09-27
forum: General Help
---

### Post by Robotman on 2008-09-27
Since installing Xubuntu on a partition on my computer, I can't access the other drives.  How would I be able to access them with full read/write permissions and have Xubuntu mount them automatically when I boot?

---

### Post by Elfy on 2008-09-27
This should help for ext3 partions, you need to add them to fstab

[http://ubuntuforums.org/showpost.php?p=5720510&postcount=5](http://ubuntuforums.org/showpost.php?p=5720510&postcount=5)

NTFS partitions the easiest way is to install ntfs-config and run the tool.

```
sudo apt-get install ntfs-config
```

For more information

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by Robotman on 2008-09-27
That first link was exactly what I needed.  I just had to visit the old partition first to get the UUIDs, then switch around the details for my specific case (ie mousepad instead of gedit).
Thanks!

---

