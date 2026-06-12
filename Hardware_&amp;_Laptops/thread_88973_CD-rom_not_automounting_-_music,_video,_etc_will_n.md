---
title: "CD-rom not automounting - music, video, etc will not play"
date: 2005-11-11
forum: Hardware &amp; Laptops
---

### Post by harty83 on 2005-11-11
Hello,

I just installed Hoary.  My cd/dvd-rom combo drive will not automount.  I can manually mount it, but it will not automount.  That wouldn't really bother me except that I cannot play music cds, dvds, and other things.  My CD or Music Player in Hoary gives a "Drive error" message.  Like I said I can read the contents of the CDs, but it won't play music CDs etc.  

Any ideas? 

My fstab is:

```
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /home           ext3    defaults        0       2
/dev/sda7       /media/storage  vfat    nodev,noexec,nosuid,gid=100,umask=007  $/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   auto    rw,user,noauto  0       0
/dev/hdc1       /media/windows  ntfs    nls=utf8,umask=0222 0   0

```

Thanks!
Alan

---

