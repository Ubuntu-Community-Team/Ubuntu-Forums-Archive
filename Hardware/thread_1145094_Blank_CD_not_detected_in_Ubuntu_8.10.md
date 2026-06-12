---
title: "Blank CD not detected in Ubuntu 8.10"
date: 2009-05-01
forum: Hardware
---

### Post by technocp on 2009-05-01
I have installed Ubuntu 8.10 since couple of months. I have been easily using my CD-ROMs to read but today i found that Blank CDs are not found to be detected.

The problem is that since Blank CD is not detected all my CD Burners won't work for writing data to CD.

Please guide me through this problem and share your experiences if any on same

Thanks
Chaitanya

---

### Post by pastalavista on 2009-05-01
Please post the output of ```
cat /etc/fstab
```

I'm guessing you installed with a USB flash drive and no CD in the CDrom drive. When I did the same, I had to edit my fstab by adding this line.> /dev/sr0 /media/cdrom0 udf,iso9660 user,noauto 0 0. You may have a different label (sr0) on your CD drive.

---

