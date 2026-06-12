---
title: "fstab issue"
date: 2008-04-05
forum: Hardware &amp; Laptops
---

### Post by GregRC on 2008-04-05
Hey guys, I'm having an issue with fstab that has me completely stumped.  

I have an external drive with an NTFS filesystem. Ubuntu will autodetect just fine when I plug it in while the system is running.  
The "mount" command tells me this..

/dev/sdc1 on /media/OneTouch4 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

I want the drive to be mounted on boot so I add the information I got from "mount" to fstab using the proper syntax.. 

/dev/sdc1 /media/OneTouch4 fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096

Yet, it still won't mount on boot. Any ideas on this? I appreciate any input

---

### Post by tamoneya on 2008-04-05
```
/dev/sdc1 /media/OneTouch4 ntfs rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
``` Try putting that into fstab

---

