---
title: "How to format internal hard drive to NTFS?"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by catchagato on 2009-01-26
I want to install Vista onto a Thinkpad. The problem comes up when I used the Windows Upgrade CD and it was not able to format my hard drive. It said that it could only format hard drives in NTFS. I am not very experienced with GParted and I tried toying around with it, but no luck. So, is there a way to format to NTFS in Ubuntu? Thanks in advance!

---

### Post by x33a on 2009-01-26
easiest way to do it would be by using gparted.

since you find it a bit hard to use. here are easy instructions:

1. open gparted.
2. if your hard drive doesn't have any partitions, click partition -> new and set the size of your choice and filesystem as ntfs.
3. if it is already partitioned, then select the first partition and click partition -> format to ntfs.

---

### Post by doglover56 on 2009-01-26
[http://linux.die.net/man/8/mkfs.ntfs](http://linux.die.net/man/8/mkfs.ntfs)

mkfs.ntfs at the command prompt should work, such as

sudo mkfs.ntfs /dev/hda3

if that is the drive you want to format.

IMF

---

### Post by catchagato on 2009-01-26
> **x33a said:**
> easiest way to do it would be by using gparted.

since you find it a bit hard to use. here are easy instructions:

1. open gparted.
2. if your hard drive doesn't have any partitions, click partition -> new and set the size of your choice and filesystem as ntfs.
3. if it is already partitioned, then select the first partition and click partition -> format to ntfs.

I am not able to select New under Partition. I have no other partitions in Ubuntu.

---

### Post by x33a on 2009-01-26
do you intend to dual boot your thinkpad, with ubuntu and vista?

or you want only vista on the thinkpad?

---

### Post by wakojakop on 2009-01-26
You guys are dooshes, he wants to modify the partition's format to ntfs. not completely reformat it,
in windows, open a commant prompt, and type CONVERT [driveletter]: /FS:NTFS
or CONVERT [driveletter]: /FS:NTFS.
it may come up with an error, say yes

---

