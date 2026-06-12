---
title: "[SOLVED] ext3 or ReiserFS on Externetal HD?"
date: 2008-06-04
forum: Hardware
---

### Post by EMCGFX on 2008-06-04
I've read this article, and it looks like it recommends [http://www.gurulabs.com/goodies/ext3_vs_reiserfs-1.php](http://www.gurulabs.com/goodies/ext3_vs_reiserfs-1.php) ext3 rather then ReiserFS.

I have 300gb old ide hard drive that I want to use for linux as a backup, its in external case connected with usb 2.0. I've used ext3 on it in the past and it worked fine. But I was wondering which one is better and faster for big backup files, like linux iso's ? The backup hd will be used for linux iso's and mix small files. Any feedback would be great, thank you.

---

### Post by Thyrus on 2008-06-04
ReiserFS is very good for many (read thousands) of very small files. For larger files you should consider something like JFS or XFS which have better allround performance than ext3 and are more geared towards larger files (or less towards small ones)

---

### Post by deanjm1963 on 2008-06-04
I've used both for my external storage. It's really "6 of one, half a dozen of the other". I've found no real speed differences between the two file systems, and I have hundreds of large files e.g. 500mb > 1.5gb and reiserFS handles them just fine. 

I checked out that article, it seems it was written in July 2002, using a system with a 2.4 kernel, I think things would have improved dramatically since that was written.

---

### Post by EMCGFX on 2008-06-05
I've decidet to stick with ext3, because I use big and small files ;) Works for me. Thanks everyone.

---

