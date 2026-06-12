---
title: "Using Testdisk for recovering USB drive"
date: 2009-07-05
forum: Hardware
---

### Post by BuntuFirstTimer on 2009-07-05
I have Ubuntu 9.04, AMD-64 computer.

My FAT32 USB drive has a problem. This is why I used TestDisk but failed.

[http://www.cgsecurity.org/wiki/Main_Page](http://www.cgsecurity.org/wiki/Main_Page)

My USB drive has errors related to permission issues and it became **read-only** default without any reasons. It wouldn't copy a complete folder and some of the files are corrupted. It's very impossible to copy them and make a fresh clean backup.

When I used TestDisk, I have a warning error like:

```
Warning: Incorrect number of heads/cylinder 128 (FAT) != 124 (HD) 
Warning: Incorrect number of sectors per track 63 (FAT) != 62 (HD) 
  FAT32                    0  18 29  1018  83 22    7830408 [KINGSTON] 
Warning: Incorrect number of heads/cylinder 128 (FAT) != 124 (HD) 
Warning: Incorrect number of sectors per track 63 (FAT) != 62 (HD) 
  FAT32                    0  18 35  1018  83 28    7830408 [KINGSTON] 
```

And I got an overall result like:


```
The harddisk (4009 MB / 3824 MiB) seems too small! (< 4009 MB / 3824 MiB) 
Check the harddisk size: HD jumpers settings, BIOS detection... 
```

I'm very clueless how to use TestDisk with a 4G USB drive. Is there a proper way to do this?

---

### Post by Christophe Grenier on 2009-07-06
Is the disk read-only or the filesystem read-only ?  TestDisk will display &quot;(RO)&quot; next to the drive size if the disk is read-only &quot;bad sectors&quot; are a possible cause.  The filesystem may be read-only if the filesystem is corrupted. Try fsck.vfat to check and repair the filesystem     Christophe  PS: You will get better results with TestDisk if in the Geometry menu you sets 128 heads and 63 sectors.

---

