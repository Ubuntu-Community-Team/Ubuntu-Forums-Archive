---
title: "Files in saved partition are unreachable and invisible?"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by MichaelBaum on 2009-11-07
I just encountered this strange pathology and wondered if anyone else had seen it and knew what to do. I just did a fresh install of Ubuntu Karmic on a Dell Notebook computer. My custom is to maintain a ~100 GB partition at the end of the hard drive for data that I'd rather not lose when I install a new system. Which I do because I have no faith in using "upgrade". So sue me.

Anyway, this partition is formatted as ext3, and I usually mount it as something in the local hierarchy, like /usr/local/archives. Normally this works. This time, I followed usual procedure, ran the Karmic install CD, chose manual partitioning, told it to _not_ format the reserve partition but rather mount it, labelled as "archive", as an ext3 partition at /usr/local/archives. 

Here's where it gets odd. None of the existing files on that partition are visible or reachable now. The directory shows no files whatsoever, hidden or otherwise -- well, there's an empty .Trash folder and a .directory file, but otherwise nothing. Regardless of being self or root. The directory free space _size_ is about what the free space would be not counting the previously existing, now invisible files. If I use the disk utility, on the other hand, it shows the correct ~100GB size. Oh, yes, and the label I asked for is not present, whatever _that_ means.

df reports about 189MByte in files on the partition. But not there. Forcing fsck on the partition causes it to create a previously missing lost-found folder (empty), but nothing else. 

Any of this mean anything to anyone?

Kthnxbai,

maab

---

### Post by scragar on 2009-11-07
If it's EXT3 it's likely a permitions problem, chown the whole directory recursively, see if that solves the problem.
```
sudo chown -R $USER: /usr/local/archive
```

---

### Post by MichaelBaum on 2009-11-07
> If it's EXT3 it's likely a permitions problem, chown the whole directory recursively, see if that solves the problem.

Well, probably not because from my original note you'll observe that even the user root, who should be able to see everything, finds no files. 

maab

---

### Post by efflandt on 2009-11-07
What is the output of **sudo fdisk -l** (print that or write it down for future reference)

Did its partion number change?  For example was it a primary partition <= 4 and now it is a logical partition >= 5?

I know from some things I just did that if what was a primary partition is now a logical partition, even starting/stopping on same exact blockx, the operating system may not be able to see it, and/or it may be a different drive number than you realize.

Actually best would be before and after listings from fdisk so you and we could tell exactly what changed. Partitions can be altered without destroying data, as long as the area where it was has not been formatted after changes

I never trust my systems to automatic partitioning since WinXP 64 beta changed my disk geometry, unable to even boot itself until I fixed it, and I recognized from numbers that SuSE output before proceeding with an installation, that it was about to do the same thing.  So I always manually set partitions and just tell the OS which existing partition(s) to use.

---

### Post by MichaelBaum on 2009-11-07
> **efflandt said:**
> What is the output of **sudo fdisk -l** (print that or write it down for future reference)

Did its partition number change?  For example was it a primary partition <= 4 and now it is a logical partition >= 5?


Well, lemmee get down to cases here.

fdisk -l reports:

 Device       Boot   Start    End   Blocks   Id   System
/dev/sda4           26760    38912  97618972+ 83 Linux

for the suspect partition. The other three, FYI, are mounted as

/dev/sda1   ext2 /boot  96358+ blocks
/dev/sda2   ext3  /   214845277+ blocks
/dev/sda3   swap  8032+ blocks

The partition index probably hasn't changed, as I always set the machine up this way.

df -h reports:
Filesystem       Size  Used  Avail   Use%  Mounted on
/dev/sda2        202G   2.4G   198G  2%    /
... yada  yada system filesystems
/dev/sda4         92G   188M   87G    1%  /usr/local/archives
/dev/sda1         89M     15M  69M   18%  /boot

Note that df is reporting 188M of used space on the partition, although all directories report that the only files there are .directory, lost+found, and .Trash-1000 (which all are empty or nearly so.)

Now, if I run fdisk on the specific weird partition (/dev/sda4)
it tells me that it's a 100.0GB partition (which contradicts the 92G report from df, above) but adds "195237944 unallocated 512-byte sectors".

Any of this help?

maab

---

