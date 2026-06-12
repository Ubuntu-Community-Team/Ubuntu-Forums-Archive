---
title: "file system compress"
date: 2012-10-02
forum: Hardware
---

### Post by th00ht on 2012-10-02
As SSD are getting more proliferate and considering that they are still restricted on size I seems to be reasonable to have transparent file system compression in the same way as NTFS supplies. Is this part of the current kernel? will it be? I'm currently writing this on a 12GB EeePC901. 
Can I use compression already?

---

### Post by rogerdpack on 2013-03-20
> **th00ht said:**
> As SSD are getting more proliferate and considering that they are still restricted on size I seems to be reasonable to have transparent file system compression in the same way as NTFS supplies. Is this part of the current kernel? will it be? I'm currently writing this on a 12GB EeePC901. 
Can I use compression already?

btrfs is included (marked as "experimental") in recent kernels, I believe, and supports some compression.

---

### Post by Cheesemill on 2013-03-20
I've been using btrfs as my primary filesystem for well over a year now, however, there is still no easy way of doing a Ubuntu installation onto a btrfs ***compressed*** drive.

The standard Ubuntu installation routine doesn't let you specify filesystem options, the only way that I've found to get Ubuntu installed with the btrfs compression option turned on is to use debootstrap after mounting the correct partitions with the compress=lzo option.

For more information, the best source (as always) is the Arch Linux wiki...

[https://wiki.archlinux.org/index.php/Btrfs](https://wiki.archlinux.org/index.php/Btrfs)

---

