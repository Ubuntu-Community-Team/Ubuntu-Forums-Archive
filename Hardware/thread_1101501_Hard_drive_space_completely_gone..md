---
title: "Hard drive space completely gone."
date: 2009-03-20
forum: Hardware
---

### Post by phearsome on 2009-03-20
Hello. I run Arch Linux and Windows SP3 on a Lenovo Thinkpad R61. I decided to move some files (around 22GB) from my Linux partition to my Windows partition. However, due to some mounting problems I am having in Arch, I decided to use my Ubuntu Live CD for this purpose.
I moved the files to my Windows partition, then I selected the files on my Arch partition and pressed Delete. Now, the files are "gone", or should I say invisible? 
The files are gone, neither Nautilus nor ls will find them. However, locate finds the files.
Nautilus claims I've got 559 MB free space, GParted claims I've got 4,28 GB free space, the Disk Usage Analyzer claims I've got 4,3 GB free space, df says I've used 70 GB out of 74 GB, and that I've got 339 MB free space.

My Linux partition is 74,66 GB, but my Disk Usage Analyzer says different. It claims on two different places that it is 74GB and 50GB.

[IMG]http://i41.tinypic.com/2rojnlh.png[/IMG]

I believe this problem might have been due to the lack of a working trash can on the Ubuntu live cd. I believe I should have used shift+delete instead, or removed them in Arch.

Well, is there any way to solve this?

---

### Post by 123456789123456789123456 on 2009-03-20
perhaps.  the fiels that were deleted, were they deleted on the windows partition or linux?

how were they moved?

---

### Post by phearsome on 2009-03-20
I moved them by mounting my Linux partition and my Windows partition, and dragging in nautilus. I am certain I removed the files on the Linux partition, and the files are still there on Windows.

---

