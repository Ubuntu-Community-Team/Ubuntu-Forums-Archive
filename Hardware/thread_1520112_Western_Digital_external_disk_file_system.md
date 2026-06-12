---
title: "Western Digital external disk file system"
date: 2010-06-29
forum: Hardware
---

### Post by fasoulas on 2010-06-29
i just bought a new external HD like this one 
```
http://www.amazon.com/Western-Digital-Elements-Portable-WDBAAR5000ABK-NESN/dp/B002CZQ4GU
```

and it's file system is ntfs.

I formated it to fat32 USING GPARTED.

Which of the 2 filesystems is better??
Is ntfs going to be regognised on other linux distros?

---

### Post by sfp100 on 2010-07-02
Hi!
I've got similar problem: I have new external disk and I'm not sure what file system to use. Points are:
* it's bigger than any disk I have - I will have no possilbility to change file system in the future
* the base is Ubuntu, but it should cooperate with other OSs
* in [ this test ]("http://www.testfreaks.com/blog/information/usb-flash-drive-comparison-part-2-fat32-vs-ntfs-vs-exfat")  FAT32 is much better than NTFS for small files. But it isn't test of external disks but pen drives.
* in  [  ntfs-3g mantainer page ](http://www.tuxera.com/products/tuxera-ntfs-commercial/performance/") one can see that ntfs-3g is much worse than ext3 and Tuxera NTFS (his commercial product)
* Somebody have wrote me, that it's possible to save linux "chmod properties" on NTFS via ntfs-3g but I haven't  (yet) understood haw it works and haw to configure

Anybody have experience/idea on this?

@fasoulas: can you change title of thread for more general, for example "what file system for portable/external disk?"
Mayby we will get more answers? 
Sorry for this "clever" question but I try to join my problem to You in place to set up new threat.

---

### Post by efflandt on 2010-07-03
FAT32 is less efficient at using space on large drives because of the cluster size, so small files may consume more space than you realize (more than shows in a directory listing).  FAT32 also has a file size limitation of 4 GB minus 1 byte, so you will not be able to use it for larger video files or DVD iso files (or BluRay images).  FAT32 has no security (no concept of permissions for specific users).  If you want to save a drive or partition image to FAT32 it would need to be broken up into multiple files (I know that at least Win7 would refuse to do back ups to FAT32).

NTFS can handle larger files and has better security.  I do not know how long there has been Linux write support for ntfs, but I think the first PC I had with ntfs was one I bought in 2004, and gparted had no trouble resizing such a partition to make room for Linux.

The only time that I have noticed Linux having any issues with any type of partition is if it has bad sectors or is otherwise already corrupted, and then if it is either FAT32 or NTFS, it will ask you to run **chkdsk /f** on it from Windows.

That being said FAT32 has the widest support for different operating systems, cameras, music players, cell phones, or USB on BluRay players or TVs, within its file size limitations.  But NTFS would be a preferred file system if you need to store any files larger than 4 GB, especially video files, backup files contained within a large file, or drive images.

---

### Post by sfp100 on 2010-07-05
@efflandt: thanks for explain difference between FAT32 and NTFS, especially lack results of big clusters on FAT32 - I have not realize this.

In topic of security for me FAT and NTFS are the same - unles I can't store unix file attributes such writing or executing (this one from chmod). It make me to use ext3 as good target for rsync archieves. Ext3 can be read on Windows via special drivers, with problem but can.

---

### Post by srs5694 on 2010-07-05
> **sfp100 said:**
> In topic of security for me FAT and NTFS are the same - unles I can't store unix file attributes such writing or executing (this one from chmod). It make me to use ext3 as good target for rsync archieves. Ext3 can be read on Windows via special drivers, with problem but can.

Neither FAT nor NTFS supports Unix-style ownership and permissions, so chmod and chown commands are useless with both of them. If you need that support, you *must* use a Linux-native filesystem, or at least a filesystem for some Unix-like OS. (There used to be a FAT driver for Linux called umsdos that added support for ownership and permissions, but it was dropped from the kernel early in the 2.6.x series, IIRC.)

---

