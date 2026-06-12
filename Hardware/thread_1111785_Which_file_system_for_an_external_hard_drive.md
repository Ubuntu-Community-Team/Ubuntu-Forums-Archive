---
title: "Which file system for an external hard drive?"
date: 2009-03-31
forum: Hardware
---

### Post by JW3 on 2009-03-31
I know that the question is regularily asked, but this is a specific variant of that question. I am considering NTFS and either XFS or ext3/4.

In essence, I am using the external hard drive 99% of the time with Linux. However, I do consider NTFS, because it would make the remaining 1% much, much easier. Having a bridge partition is always a pain.

Regarding NTFS, I am worried about two things:

[LIST]
[*]Reliability: this is the #1 issue. If there is a problem with the drive, I must know it right away. How does NTFS with ntfs-3g compare with other file systems?
[*]Performance of the ntfs-3g driver; according to [http://www.ntfs-3g.org/performance.html](http://www.ntfs-3g.org/performance.html), it is significantly lower -- on the other hand, it seems to be much better than it used to be; furthermore -- how does the existence of the additional fuse layer hit the performance of the driver? Is there an issue with defragmentation? (I have not a Windows install myself)
[/LIST]

So, what are your experiences? Who switched from NTFS or to NTFS and why?

Regards,
j.

---

### Post by CTRLurself on 2009-03-31
Honestly, I've always done a small ext3 partition for ubuntu and it's software to live on, an NTFS partition for windows to live on, and then the rest of my hard drive goes into NTFS.

For software, it's all about performance in the local OS (I don't care how well Windows apps run in linux) hence using the native filesystem. For data (documents, music, movies) it takes nowhere near the full throughput of a drive to open these very quickly (when will opening a massive 8MB word document require the 50-odd MB/s read+write speed of a drive).

And in NTFS I haven't really had any major issues with it sharing except for one covered in this discussion: [http://ubuntuforums.org/showthread.php?t=897970](http://ubuntuforums.org/showthread.php?t=897970) however it is an issue when sharing one partition between ANY two OSs.

hope this helps

~CTRL

---

