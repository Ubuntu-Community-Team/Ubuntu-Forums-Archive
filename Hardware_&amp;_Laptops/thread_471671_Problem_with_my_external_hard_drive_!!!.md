---
title: "Problem with my external hard drive !!!"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by kamikazi on 2007-06-12
when i plug my HD in i still can access it , open file or do something , but I cannot del files , move or rename files .... it said "you dont have permissions to write on this drive.." which mean this drive just read-only .... how can i fix it ??? i just a newbie with linux :P thank for your help :D

---

### Post by Gausian on 2007-06-12
if the drive is formated as NTFS you'll want to look into installing ntfs-3g.

then you wont have any more problems.

---

### Post by taurus on 2007-06-12
If your external harddrive is ntfs filesystem, then you need to install ntfs-3g driver to write/delete stuff from it.  

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by kamikazi on 2007-06-12
oh is it .. very fast support :D many thank for that :D

I tried it but it still the same :(

---

### Post by taurus on 2007-06-12
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
df -h
```

---

