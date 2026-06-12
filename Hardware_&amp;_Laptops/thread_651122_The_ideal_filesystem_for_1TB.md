---
title: "The ideal filesystem for 1TB"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by Skerit on 2007-12-27
I'm ready to buy my first terabyte HDD, which would simply **double** my current free space!

But then I started thinking about something I haven't paind enough attention to over the past few years ...

I really WANT a partition that's one terabyte big, as I just moved to recording HD video and all that space comes in handy, but isn't there some catch to such big filesystems?

Doesn't the space get *lost* somehow, something about those pesky inodes? (However, I do believe when you only put BIG files on the disk it doesn't really matter...)

---

### Post by mellowd on 2007-12-27
Remember that the harddrive is 1 TB while filesystems generally show free space as 1TiBi so you'll always lose some 'in translation'

---

### Post by Bachstelze on 2007-12-27
As far as I know, there is absolutely no drawback in having large filesystems (actually, 1 TiB is not *that* large)

About the filesystem, XFS seems the best choice for storing lots of large files. JFS also seems a good candidate, but it has not been as thouroughly tested as XFS, having been around for less time. Otherwise, good ol' ext3 will do the job pretty well too.

---

### Post by Skerit on 2007-12-27
Sure, I know it won't be one TiBi (something I just couldn't understand so many years ago, hehe) 

It's hard to find a decent chart out there, to convert tebibyte to gigabyte, for example, but 1 TB should be 931.32 GiB, so 0.91 TiB

(I still don't understand why people suddenly said the decimal way is the "most correct" way of counting bytes, but that's a completely different discussion.)

Anyway, thanks for the information!

---

