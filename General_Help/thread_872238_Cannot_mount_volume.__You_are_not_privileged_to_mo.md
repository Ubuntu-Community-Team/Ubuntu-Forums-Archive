---
title: "Cannot mount volume.  You are not privileged to mount this volume."
date: 2008-07-27
forum: General Help
---

### Post by morbid_bean on 2008-07-27
"Cannot mount volume.  You are not privileged to mount this volume."  
is what i get when i try to access my hard drives

was working fine untill i installed wine and a few programs...what happend!

---

### Post by terry f on 2008-07-27
use the command ```
sudo fdisk -l
``` find the dev name.  then ```
sudo mkdir /media/disk
``` then try ```
sudo mount /dev/YOUR_DRIVE_NAME /media/disk
```

---

