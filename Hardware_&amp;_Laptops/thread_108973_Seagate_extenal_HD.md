---
title: "Seagate extenal HD"
date: 2005-12-27
forum: Hardware &amp; Laptops
---

### Post by pronto185 on 2005-12-27
Edit :
i was able to get it working 




I got a extranl HD , but when i plug it in it wont let me veiw it 
how to get it so it can be used?
its the 400gb on
the 40gb is in my laptop , witch works
sudo fdisk -1 ```
justin@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4662    37447483+  83  Linux
/dev/hda2            4663        4864     1622565    5  Extended
/dev/hda5            4663        4864     1622533+  82  Linux swap / Solaris

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

```

Btw . im a linux noob , so yeah

---

