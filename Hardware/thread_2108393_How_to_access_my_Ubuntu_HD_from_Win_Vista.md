---
title: "How to access my Ubuntu HD from Win Vista"
date: 2013-01-24
forum: Hardware
---

### Post by Jayzif on 2013-01-24
Hi there,

I've just installed Ubuntu onto a second hard drive. What I would like to be able to do is swap files between my two hard drives. My primary hard drive is running Win Vista (crap, I know lol).

Upon booting up my Vista drive I am able to find the Ubuntu hard drive in Device Manager but I cannot access it from My Computer, has any one got any tips for me? do I somehow need to assign the second drive a letter? I think I've heard before that Windows doesn't like working with drives that aren't NTFS formatted?

Many thanks :p

---

### Post by ahallubuntu on 2013-01-24
Windows can't access Linux partitions natively, whereas Ubuntu can access Windows partitions (NTFS, FAT32) natively.

There is a Windows driver to access ext2/ext3 partitions within Windows - doesn't work for ext4 as I recall (and you probably used ext4 when you installed Ubuntu - that's the default).  In any case, I had mixed luck with the ext3 driver in Windows when I used it.  It had some quirks.  By contrast, the NTFS access of Windows partitions within Linux is very solid - I've used it for years.

So what I suggest you do is share all your files on an NTFS partition that Windows can access and so can Ubuntu.

If the case is that your new Ubuntu drive is much larger than the old Vista drive, there are things you can do such as making a large NTFS data partition on the Ubuntu drive and devoting only a small space for the  operating system.  Honestly, 20GB has been plenty for me recently in installing Ubuntu 12.04, provided you are saving your data not in /home but on some other partition.

---

