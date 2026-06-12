---
title: "only 185 GB on formatted 200 GB HD"
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by RaiSuli on 2006-03-02
Hi,

after formatting my external 200 GB hard drive with ext3 only 186 GB show up. I know that a small loss of storage space isn't unusual, but 14 GB sounds a bit much. Is this normal?

---

### Post by matthew on 2006-03-02
This will explain some of it for you: [http://en.wikipedia.org/wiki/Gigabytes]("http://en.wikipedia.org/wiki/Gigabytes")

It has to do with how hard drive sizes are reported/advertised and the differing definitions of "gigabyte," eiter as a power of 10 or a power of 2. A new term Gibibyte has been created to help with the confusion.

---

### Post by cylon359 on 2006-03-02
ext2/3 reserve 5% of the filesystem for root only.  With disks these days being really big, this is a bit excessive.  With 200 GB, that's 10 GB gone right there.

You can set it to 1% using tune2fs:

$ sudo tune2fs -m 1 /dev/whatever_your_filesystem_is

I've heard that setting it to 0% is bad as it can't auto defrag as efficient.

---

### Post by RaiSuli on 2006-03-02
Thanks for the quick and interesting answers. Wasn't aware of these issues before.

---

