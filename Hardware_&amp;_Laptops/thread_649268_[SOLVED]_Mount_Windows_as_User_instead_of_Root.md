---
title: "[SOLVED] Mount Windows as User instead of Root"
date: 2007-12-24
forum: Hardware &amp; Laptops
---

### Post by werdna5225 on 2007-12-24
I have a dual boot system.  My Windows drive has 3 partitions and all 3 are mounted on logon, however, the drive is owned by root so I can only read the drive I cannot write to it.  How can I change the permissions of the drive so I can read and write to it?

---

### Post by eggdeng on 2007-12-24
If the drives are formatted in ntfs, you need to install ntfs3g to have write access. See [https://help.ubuntu.com/community/MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")
for the steps to follow.

---

### Post by Rocket2DMn on 2007-12-24
You should keep the mount points owned by root, but you can have access to them with ntfs-3g as suggested.
You will have to enable read/write with ntfs-3g, then add/modify the lines in your /etc/fstab file.  They should look something like this (though your device and mount point will be different)
```
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```
With that I have my windows partition (sda1) mounted at /media/windows and I have full read/write permissions.  Don't forget to remount after changing the file
```
sudo mount -a
```

---

### Post by werdna5225 on 2007-12-24
Figured it out.  Installed ntfs3g.  Then I edited my /etc/fstab from 

/dev/hda1 /media/hda1 ntfs-3g **defaults**,locale=en_US.UTF-8 0 0

to

/dev/hda1 /media/hda1 ntfs-3g **rw,user,**locale=en_US.UTF-8 0 0

I then restarted and I have read and write access.

---

