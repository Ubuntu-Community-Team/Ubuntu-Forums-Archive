---
title: "connecting linux drive in vista"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by sarracenia88 on 2007-05-03
I would like to know how I can find my ubuntu 7.04 partition in windows vista. It is not seen under my computer.  I have not used windows in a longtime so I am a little out of practice. My mind has started thinking in ubuntu terms (I believe that this is a good thing?) So anyways, I want to access the files on my linux partition in vista, which is on a separate partition.

Thanks,

---

### Post by garlik42 on 2007-05-03
Because your linux partitions are ext3 based, you need a file system driver that allows windows to talk other than the FAT32/NTFS it currently knows about.

I know of 2 solutions that work with pre-vista machines, I have not tested either with vista (only xp)

This product will allow you to mount the ext2 file system directly as a drive letter in windows
[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

This product will allow you to brows without directly mounting the drive (maybe a bit safer)
[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

As I said, I don't know if they will work with Vista, check the websites.

Good luck.

---

