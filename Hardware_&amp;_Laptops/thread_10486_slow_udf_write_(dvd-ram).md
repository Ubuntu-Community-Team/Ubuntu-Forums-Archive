---
title: "slow udf write (dvd-ram)"
date: 2005-01-08
forum: Hardware &amp; Laptops
---

### Post by droebbel on 2005-01-08
I know writing on DVD-RAM reaches just half the reading speed because of data verification. 

I had problems though with writing speed being way too low with two drives, a LG 4120 and a LG 4163.  The "official" speed of both drives and the disks is 3x. Reading ist OK: 3.92MB/s. So Writing should be about 1.9MB/s.

But with both drives writing reaches no more than about 1MB/s with the ubuntu kernels I tried. (2.6.8.1 image; 2.6.9.and 2.6.10 built from the sources in hoary)

I reached about 1.9 MB/s with a 2.6.7-kernel from my old gentoo installation.

Have there been any changes in recent kernels that might explain the problem (I didn't find anything I understood in the changelogs, but there was a lot of udf stuff)?

I do not really want to use that old kernel, as it seems to lack some necessary features and might have security issues. Any idea how to make it work with a current kernel built from ubuntu sources, maybe with a patch?

---

### Post by droebbel on 2005-02-08
Some additions:

It is not a udf problem, same thing with ext2.

The settings for the io-scheduler are the same with both kernels.

Some changes in block device handling or so? I don't know anything about that.

Still searching for an idea.

[Edit:]
It ist getting more and more confusing: raw writing iwith dd is much faster..
1G write to /dev/scd0: 12min
1G write to file: 19min.

When writing to a file, the head of the drive seems to be moving quite a lot.
No other files on the disk of course...

---

