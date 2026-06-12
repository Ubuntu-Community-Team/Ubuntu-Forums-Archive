---
title: "moving from ntfs to xfs"
date: 2008-09-13
forum: General Help
---

### Post by tone33 on 2008-09-13
So I'm in the process of moving everything to linux.  I have several gigs of vides, music and pictures that are currently on NTFS partitions.  I want to move these to XFS partitions (I think - unless another FS is better suited for this).  can i just copy them from NTFS to XFS?  or do i need to convert them?  How does this work?

---

### Post by Pro-reason on 2008-09-13
That conversion is not possible on-the-fly, I believe.

Move your data elsewhere, reformat with the new filesystem, then put the data back.

I'd generally prefer ext3 over xfs, but perhaps you have some reason for using it.

---

### Post by tone33 on 2008-09-13
that is what i was planning to do, so if i move the data elsewhere..  say to another NTFS partition, and then move it back, no conversions are needed?  I'm slightly confused as I thought the data is saved to disk based on the filesystem that disk is formatted to.  Thus the incompatibility of NTFS with ext3 or XFS.  Maybe I'm just missing the fundamentals here though...

Any reason ext3 is better than XFS?  I'm fairly new to linux so i don't really know which to choose at this point.

---

### Post by HermanAB on 2008-09-13
You just copy the data over - click drag drop with Nautilus.

However, NTFS is pretty good file system, so I would just leave it there.

---

### Post by Pro-reason on 2008-09-13
> **tone33 said:**
> that is what i was planning to do, so if i move the data elsewhere..  say to another NTFS partition, and then move it back, no conversions are needed?  I'm slightly confused as I thought the data is saved to disk based on the filesystem that disk is formatted to.  Thus the incompatibility of NTFS with ext3 or XFS.  Maybe I'm just missing the fundamentals here though...

Any reason ext3 is better than XFS?  I'm fairly new to linux so i don't really know which to choose at this point.

I don't know why you say &#8220;no conversions are needed&#8221;.  I said that you needed to reformat the partition with the new filesystem (*[XFS]("http://en.wikipedia.org/wiki/XFS#Disadvantages")* or *[ext3]("http://en.wikipedia.org/wiki/ext3")*).  Since this will destroy all data, you need to move or back up all the data to another location while you are doing this.  Do it for each partition in turn.

*Ext3* is the standard Linux filesystem.  That's why I recommend it.  You can use [others]("http://en.wikipedia.org/wiki/Comparison_of_file_systems") if you like.  I personally use the slightly more avant-garde *[ReiserFS]("http://en.wikipedia.org/wiki/ReiserFS")* for my Ubuntu root partition, and *ext3* for all additional partitions, including USB thumbdrives.  One advantage that *ext** (version [2]("http://en.wikipedia.org/wiki/ext2") or [3]("http://en.wikipedia.org/wiki/ext3")) has over *reiserfs/XFS/JFS* is that you can install *ext** [drivers on Windows]("http://www.fs-driver.org/") so that Windows can access those partitions.

I always warn against using *ntfs* on Linux, because it is not an open standard.  It is a trade secret of Microsoft's, and has only recently been cracked open enough for us to use *ntfs* filesystems with a measure of confidence.  I still see people on these forums with problems caused by this filesystem.  It's just evil.

---

### Post by tone33 on 2008-09-13
> **Pro-reason said:**
> I don't know why you say “no conversions are needed”.  I said that you needed to reformat the partition with the new filesystem (*[XFS]("http://en.wikipedia.org/wiki/XFS#Disadvantages")* or *ext3*).  Since this will destroy all data, you need to move or back up all the data to another location while you are doing this.  Do it for each partition in turn.

*[Ext3]("http://en.wikipedia.org/wiki/ext3")* is the standard Linux filesystem.  That's why I recommend it.  You can use [others]("http://en.wikipedia.org/wiki/Comparison_of_file_systems") if you like.  I personally use the slightly more avant-garde *[ReiserFS]("http://en.wikipedia.org/wiki/ReiserFS")* for my Ubuntu root partition, and *ext3* for all additional partitions, including USB thumbdrives.  One advantage that *ext** (version [2]("http://en.wikipedia.org/wiki/ext2") or [3]("http://en.wikipedia.org/wiki/ext3")) has over *reiserfs/XFS/JFS* is that you can install *ext* [drivers on Windows]("http://www.fs-driver.org/") so that Windows can access those partitions.

I always warn against using *ntfs* on Linux, because it is not an open standard.  It is a trade secret of Microsoft's, and has only recently been cracked open enough for us to use *ntfs* filesystems with a measure of confidence.  I still see people on these forums with problems caused by this filesystem.  It's just evil.



So i backup/move data off the current ntfs partition, and then create my new ext3 partition, and then move data to newly created ext3 partition - since this data was stored on an NTFS partition initially will there be any issues when i copy it to the new ext3 partition?  That's my point of confusion right now...

I do indeed want to move away from NTFS and to a linux filesystem...just trying to understand my options at this point.  Thanks for your insight here.

---

### Post by Pro-reason on 2008-09-13
> **tone33 said:**
> since this data was stored on an NTFS partition initially will there be any issues when i copy it to the new ext3 partition?  

When moving files from one partition to another, you can lose information such as ownership and permissions if the new filesystem does not support them.  This will happen if you move files from an *ext3* system to a *FAT* system, for example.

This shouldn't normally be an issue when moving from *NTFS* to *ext3*.

However, if you wish to make sure that all such information is exactly preserved, no matter what system you are moving to and no matter what method you use for transferring the actual data, then you should put the data into an [archive]("https://help.ubuntu.com/community/BackupYourSystem") file.

To do this, use a command such as *[tar]("https://help.ubuntu.com/community/BackupYourSystem/TAR")*.

If you want to back up the contents of */media/movies* to an archive on */media/backup*, then do the following:

```

sudo apt-get install lzop
**tar -cv /media/movies | lzop > /media/backup/movies.tar.lzo**

```

The *lzop* command provides file compression that is scarcely slower than writing uncompressed data to disk.  (*gzip* would probably be a mistake because it would slow things down so much.)

Obviously, verify your archive before formatting your drive.

---

### Post by tone33 on 2008-09-13
ok i understand now.  thanks.

---

