---
title: "Best filesystem for new laptop"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by tom66 on 2009-03-21
I will be getting a new laptop soon - yay!

Anyway, I've always been an ext3 user, but I've heard it's slower than some other file systems. With a 250 GB SATA 5400 RPM hard disk drive (160 GB for Ubuntu, and partitions for Vista (ugh) and swap), and an Intel Core 2 Duo (2.0 GHZ, 1 MB L1 cache) processor with 3 GB RAM, what would be fastest and lightest (CPU-wise and disk-wise) file system for this laptop? I've been considering ReiserFS.

Also, can people recommend a swap size for this laptop?

---

### Post by Cruncher on 2009-03-21
I don't know about the speed, but if I remember correctly with ext3 it is not possible to powerdown the harddisk after a certain time of inactivity to conserve power, because it is a journaling file system which accesses the disk every few seconds. With ext2 on the other hand, the hard disk can power down if not in use.

---

### Post by sgosnell on 2009-03-21
You might want to try ext4, if you're willing to go with cutting-edge stuff.  You'll need to run Jaunty, but it has been very stable for me.

---

### Post by tommcd on 2009-03-21
See this page for some interesting benchmark tests of file systems:
[http://linuxgazette.net/102/piszcz.html](http://linuxgazette.net/102/piszcz.html)
It does not include ext4 though. I will be trying ext4 when Jaunty comes out.
See this thread about ext4. Read post #2 about "delayed allocation" in ext4:
[http://bbs.archlinux.org/viewtopic.php?id=67786](http://bbs.archlinux.org/viewtopic.php?id=67786)

---

### Post by tom66 on 2009-03-21
I would like to stick with the most stable releases, if possible. So is ext3 really the fastest file system for basic use then?

---

### Post by tommcd on 2009-03-22
> **tom66 said:**
> I would like to stick with the most stable releases, if possible. So is ext3 really the fastest file system for basic use then?

Ext3 is said to be the most stable linux file system. XFS is said to handle large files better (faster) than ext3. I have heard people say the XFS and ReiserFS are faster than ext3. If you want ultimate stability and reliability, ext3 is hard to beat. There have been a number of times over the last few years that my system locked up and I had to do a hard reboot by pressing the power button. I use ext3 and never had any data corruption or data loss.
Ext4 is said to be faster than ext3 because (among other things) it uses delayed allocation like XFS and ReiserFS. Read the caveat about delayed allocation in the thread from the Arch forums I linked to in my last post. You should have your system on a UPS (battery backup) to guard against data loss if you try ext4 with Jaunty because you could potentially loose data that has not been written to disk yet if the power goes out. Delayed allocation can delay the writing of data to disk be up to 30 seconds to increase speed. You can also add the **nodealloc** option to the mount options for ext4 to disable delayed allocation. This will cause a slight performance hit, but should still be faster than ext3 from what I have read.
Also see these:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4](http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4)
[http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1](http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1)

---

