---
title: "Format for external hard drive to be shared between Ubuntu and Mac OS X"
date: 2017-07-14
forum: Hardware
---

### Post by flucoe2 on 2017-07-14
Hi,

I recently bought a 8 TB external drive to be used as an additional back up alternative. I want to be able to use it both in Ubuntu and in OS X. I thought that UDF would be the way to go but it seems it only works up to 2 TB (I was using [https://github.com/JElchison/format-udf](https://github.com/JElchison/format-udf)). As I don't want to go from an 8TB drive to a 2TB one, I need to find a different approach. Is there a format that would allow me to read/write in Ubuntu (16.04 for now) and Mac OS X and i) use the full capacity of the hard drive and ii) allow to transfer files larger than 2GB (so, FAT32 is out)?

Thanks.

---

### Post by yancek on 2017-07-14
Try ntfs.  Linux systems support read/write to ntfs partitions as long as you have ntrs-3g installed.  Mac OSX apparently does also but it isn't enabled by default.  Check the link below.

[https://www.cnet.com/news/how-to-manually-enable-ntfs-read-and-write-in-os-x/](https://www.cnet.com/news/how-to-manually-enable-ntfs-read-and-write-in-os-x/)

---

### Post by gsahli on 2017-07-14
exFAT is another choice:
[https://www.howtogeek.com/235655/how-to-mount-and-use-an-exfat-drive-on-linux/](https://www.howtogeek.com/235655/how-to-mount-and-use-an-exfat-drive-on-linux/)
[http://lifehacker.com/5927185/use-the-exfat-file-system-and-never-format-your-external-drive-again](http://lifehacker.com/5927185/use-the-exfat-file-system-and-never-format-your-external-drive-again)
BTW - Mac OS Sierra and ubuntu can create exFAT partitions.

---

### Post by kurt18947 on 2017-07-14
Not a Mac guy but this post made me curious. This might be of some interest. It's from December 2014 but it may have applicability:

[http://www.macworld.com/article/2855038/how-to-mount-and-manage-non-native-file-systems-in-os-x-with-fuse.html](http://www.macworld.com/article/2855038/how-to-mount-and-manage-non-native-file-systems-in-os-x-with-fuse.html)

---

### Post by flucoe2 on 2017-07-17
Thanks for the suggestions.

---

