---
title: "NTFS partition not writable"
date: 2007-02-01
forum: Hardware &amp; Laptops
---

### Post by WardLoockx on 2007-02-01
Hello,

I bought me an ICY box and connected it to my (k)ubuntu. I can acces the 2 ntfs partitions without a problem, but when I try to delete I get a message telling me I haven' t got the priviliges. Should I mount it different?

> 
ward@ward:/media/sdc5$ rm -rf temmp/
rm: cannot remove `temmp//VIDEO_TS.BUP': Read-only file system
rm: cannot remove `temmp//VIDEO_TS.IFO': Read-only file system
rm: cannot remove `temmp//VIDEO_TS.VOB': Read-only file system
rm: cannot remove `temmp//VTS_01_0.BUP': Read-only file system
rm: cannot remove `temmp//VTS_01_0.IFO': Read-only file system
rm: cannot remove `temmp//VTS_01_0.VOB': Read-only file system
rm: cannot remove `temmp//VTS_01_1.VOB': Read-only file system
rm: cannot remove `temmp//VTS_01_2.VOB': Read-only file system
rm: cannot remove `temmp//VTS_01_3.VOB': Read-only file system
rm: cannot remove `temmp//VTS_01_4.VOB': Read-only file system
rm: cannot remove `temmp//VTS_01_5.VOB': Read-only file system



Thanks,
Ward

---

### Post by Jagot on 2007-02-01
NTFS is not writable by default in Ubuntu.  Have you installed ntfs-3g?

[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite#head-895b18672ca641915baef5242794e5370702ba36](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite#head-895b18672ca641915baef5242794e5370702ba36)

---

