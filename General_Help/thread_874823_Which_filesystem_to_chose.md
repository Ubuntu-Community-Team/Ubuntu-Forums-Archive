---
title: "Which filesystem to chose?"
date: 2008-07-30
forum: General Help
---

### Post by malfist on 2008-07-30
I've been using JFS as my filesystem for the past year or so and I love it. However, it's big thing is less CPU usage, but not necessarily faster I/O. However, I just bought a quad core, and CPU usage is no longer an issue, however seek times on my hard drives are.

Does anyone know what the best filesystem to use for computers that just need faster I/O and don't really care about CPU usage?

Malfist

---

### Post by finite9 on 2008-07-30
is there such a huge difference in CPU usage between filesystems?  Do you have applications that really need to save on cpu cycles on the filesystem?  If you dont really have specific applications that depend heavily on FS, then it is always best to stick with ext3.

---

### Post by malfist on 2008-07-30
EXT2/3 is 2-3 times slower than JFS and raiser3 and XFS, and consume far more reasources. While JFS my be slightly slower than raiser or XFS, it's about twice (if I remember correctly) the speed of EXT3 with less than a 1/3 of CPU usage.

From all the benchmarks I've seen EXT2/3 are some of the slowest filesystems outside of FAT16/32. (No data on NTFS)

---

### Post by SunnyRabbiera on 2008-07-30
It depends, for me ext3 is speedy fast.

---

### Post by malfist on 2008-07-30
May information is slightly incorrect:
[http://linuxgazette.net/122/TWDT.html#piszcz](http://linuxgazette.net/122/TWDT.html#piszcz)

I've found a lot of data saying that Raiser is much much faster than the other FS's, but then those pages also accuse the Kernel Devs of attempting to sabotage raiser and jews of setting up raiser's creator, those pages might not be totally truthful.

EXT3 isn't as bad as I thought it was, but it's far from the best.

---

### Post by bodhi.zazen on 2008-07-30
All these discussions about file systems focus on "speed".

I do not find a noticeable difference in how snappy a system feels based on the filesystems and you should take the various benchmarks with a (large) grain of salt.

[http://linuxgazette.net/102/piszcz.html](http://linuxgazette.net/102/piszcz.html)

Look at those tests, touching 10,000 files, removing 10,000 files. Quite artificial, IMO. Also depending on the benchmark one or another file system is best.

You should understand the other features of file systems including reliability, cross platform compatibility, features, ect.

In general, IMO, most desktop users should stay with ext3 and unless you are performing a specialized task over and over you are unlikely to see much difference in overall system speed based on underlying file systems.

[http://linuxmafia.com/faq/Filesystems/journaled-filesystems.html](http://linuxmafia.com/faq/Filesystems/journaled-filesystems.html)

---

### Post by articpenguin on 2008-07-30
I find JFS XFS more fast than ext3. Ext3 uses a classic block mapping tradition. This is efficent for small files. But for large files its a problem, that is why deleting large files on ext3 are real slow. 

JFS and XFS use extents. Extents are more efficient than than the block mapping tradtion that ext3 uses. JFS and XFS delete large files almost instantly compared to EXT3.


JFS and XFS also allocate Inodes dynamically. This way you are not stuck with millions of unneeded inodes like ext2/ext3. ext2/3 all allocate inodes at mkfs time. On my 480GB partition i have 28Million inodes and i only use about 2 million. All those inodes cost me about 6-8GB of space with each inode 256 bytes.

---

