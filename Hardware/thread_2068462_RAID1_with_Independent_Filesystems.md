---
title: "RAID1 with Independent Filesystems?"
date: 2012-10-09
forum: Hardware
---

### Post by catlover2 on 2012-10-09
Has anyone ever heard of a way to synchronize multiple filesystems while keeping them completely independent? For example, suppose I have three identical drives with one EXT4, one HFS+, and one XFS partition, respectively. If I write something to the HFS+ drive, I want that file to be immediately written to the other two. 

I know I could just add a simple rsync script to cron, but I like the idea of everything happening instantly.

Thanks!

-catlover2

---

### Post by papibe on 2012-10-09
Hi catlover2.

Take a look at [Unison]("http://www.cis.upenn.edu/~bcpierce/unison/") (it is in the repositories BTW).

Let us know how it goes.
Regards.

---

### Post by catlover2 on 2012-10-10
I *think* that's exactly what I'm looking for; I'll let you know when I try it out.

---

