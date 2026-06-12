---
title: "Is my external hard drive slow?"
date: 2010-06-17
forum: Hardware
---

### Post by stinkinrich88 on 2010-06-17
Hello,

I just bought a Western Digital Elements hard drive (2TB). I created an MSDOS partition table, then formatted it to NTFS. 

My computer is fast and modern with USB 2.

The website: [http://wdc.com/en/products/Products.asp?DriveID=762](http://wdc.com/en/products/Products.asp?DriveID=762) says the data transfer speed should be 480Mb/s (max) so I take it this is about 60MB/s (1 megabyte = 8 megabits). 

I'm transferring my DVDs onto my new drive and it's only going at 7.6 MB/s. Does this seem too slow? Have I got a faulty drive?

Thanks

---

### Post by dabl on 2010-06-17
File transfer speed via USB has been an issue for some time, and there are only partial improvements available, via changing the kernel scheduler option:

[http://ubuntuforums.org/showpost.php?p=8010056&postcount=270](http://ubuntuforums.org/showpost.php?p=8010056&postcount=270)

[http://ubuntuforums.org/showpost.php?p=8124833&postcount=294](http://ubuntuforums.org/showpost.php?p=8124833&postcount=294)

---

### Post by stinkinrich88 on 2010-06-17
Thanks for the reply, dabl. That's a big shame. Do you know if there are any quick-fixes? I.e. do you know of a liveCD distro that doesn't suffer from this problem, which I can use to transfer my files? (I can't use windows because my files are saved on an ext3/4 partition)

Thanks

---

### Post by stinkinrich88 on 2010-06-17
Actually, I just installed drivers to read ext3 in windows xp, but the data transfer seemed just as slow! It took about 5 minutes to transfer 4.3gb (my calculations estimate 73 seconds at 60MB/s). Strange.

Although, I definitely get decreasing rates in Ubuntu. It starts at about 33MB/s and gets lower and lower over time.

---

### Post by dabl on 2010-06-17
Among the several Linux distributions that I have used, and using default/stock kernels, I don't see a noticeable difference in USB transfer speed.  I use a large (and not terribly fast) Samsung hard drive, in a USB enclosure, for backups, and it doesn't seem to go any faster from one computer to the next.

I also think the problem is a little more complex than just the speed across the USB channel, especially with memory sticks.  Most of them are not that fast at writing -- so I suspect the big file transfers end up waiting for the write to happen on the target stick.  At least that is my suspicion -- apparently it's not enough of a problem that I care to spend the time benchmarking them.  :lolflag:

---

