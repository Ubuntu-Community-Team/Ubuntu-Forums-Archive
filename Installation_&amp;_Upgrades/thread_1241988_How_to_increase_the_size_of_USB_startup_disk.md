---
title: "How to increase the size of USB startup disk?"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by matthew_exon on 2009-08-16
I created a USB startup disk on a 1GB stick and ran out of space.  I've copied the files over to a 4GB stick but I still have no space.  Does anyone know how to increase the size of the persistent data file so it uses up the remaining space on the stick?

Thanks,
Mat

---

### Post by Yvan300 on 2009-08-16
Go back through the setup again and this time increase the size that is allocated to your files :)

---

### Post by matthew_exon on 2009-08-17
That would trash all my settings.  Is there any way to increase the size without trashing my settings?

---

### Post by matthew_exon on 2009-08-17
OK, I figured it out.  I found that the casper-rw file is the one that holds the saved data, and it's just an ext3 image file.  So I found [these instructions]("http://pookey.co.uk/blog/archives/36-resizing-a-ext3-disk-image.html") for resizing ext3 partitions, and used a different Ubuntu USB key to do it:

```
ubuntu@ubuntu:/media/disk$ dd if=/dev/zero bs=1M count=2800 >> casper-rw
2800+0 records in
2800+0 records out
2936012800 bytes (2.9 GB) copied, 465.675 s, 6.3 MB/s
ubuntu@ubuntu:/media/disk$ e2fsck -f casper-rw 
e2fsck 1.41.4 (27-Jan-2009)
...
casper-rw: ***** FILE SYSTEM WAS MODIFIED *****
casper-rw: 2669/73728 files (11.1% non-contiguous), 277618/294800 blocks
ubuntu@ubuntu:/media/disk$ resize2fs casper-rw 
resize2fs 1.41.4 (27-Jan-2009)
Resizing the filesystem on casper-rw to 3162000 (1k) blocks.
The filesystem on casper-rw is now 3162000 blocks long.

ubuntu@ubuntu:/media/disk$ e2fsck -f casper-rw 
e2fsck 1.41.4 (27-Jan-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
casper-rw: 2669/790528 files (11.1% non-contiguous), 369213/3162000 blocks
```

---

