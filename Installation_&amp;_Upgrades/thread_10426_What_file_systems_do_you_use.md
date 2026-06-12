---
title: "What file systems do you use?"
date: 2005-01-07
forum: Installation &amp; Upgrades
---

### Post by BORTKOMMEN on 2005-01-07
Which filesystem do you use in Ubuntu. Are there any options during installl, and if that is the case which of them do you prefer. Reisers, Jfs, ext3?

There are certainly as many opinions as there are users but I want to here them anyway, before I begin with the installation.

2. By the way I cannot see any tutorials here:

[http://www.ubuntulinux.org/support/documentation/tutorial/tutorialfolder_view](http://www.ubuntulinux.org/support/documentation/tutorial/tutorialfolder_view)

---

### Post by rbrimhall on 2005-01-07
reiserfs, not sure why... it seems faster to me for some reason...

---

### Post by rider343 on 2005-01-07
xfs :)

---

### Post by CompShrink on 2005-01-07
ext3

Why? Because it's rather universal, it can be read by prettymuch any recovery disk you use that will work with *nix, and doesn't have the resizing issues reiserfs can have with some partitioning software.

---

### Post by fng on 2005-01-07
hda1 : ext2
hda2 : ext3
hdc1 -> hdf1 : reiser

---

### Post by wallijonn on 2005-01-08
I've heard that with reiserfs the hard disk drive is always spinning, so I went with Ext3.

---

### Post by drake on 2005-01-08
ext3

---

### Post by JsPr on 2005-01-08
ReiserFS 3.6

---

### Post by alpha on 2005-01-08
[QUOTE=JsPr]ReiserFS 3.6[/QUOTE]
 What are the difference between these file systems?

---

### Post by tiiim on 2005-01-08
[QUOTE=alpha]What are the difference between these file systems?[/QUOTE]
 im not sure wot the differences are but i choose reiserfs i find its faster of handling stuff and excellent for compiling and system searches and upon shutdown or powercut its recovering time beats ext3.

what is xfs like compared to this?

---

### Post by zeroK on 2005-01-10
[QUOTE=BORTKOMMEN]Which filesystem do you use in Ubuntu. Are there any options during installl, and if that is the case which of them do you prefer. Reisers, Jfs, ext3?

There are certainly as many opinions as there are users but I want to here them anyway, before I begin with the installation.

2. By the way I cannot see any tutorials here:

[http://www.ubuntulinux.org/support/documentation/tutorial/tutorialfolder_view](http://www.ubuntulinux.org/support/documentation/tutorial/tutorialfolder_view)[/QUOTE]
 I will probably switch to Ext3 in the evening because XFS is (at least for me) far to unstable. After a small crash last night I've lost my whole ~/.thunderbird folder and my ~/.mozilla folder got corrupted.

I've used ReiserFS (3) for more than 1.5 years and it's really fast. But don't make your hdd full, or you will have to repair your partition.

So I'll probably go with the slowest but most stablest here *g

---

### Post by Bogart on 2005-02-09
I was trying to choose a filesystem and found some interesting tests:

[http://linuxgazette.net/102/piszcz.html](http://linuxgazette.net/102/piszcz.html)

[http://www.potentialtech.com/wmoran/postgresql.php](http://www.potentialtech.com/wmoran/postgresql.php)

ext3 seems the slowest, while reiserfs and jfs seem the fastest.

However, this is just about performance, which is not the only thing to value. I have no idea how stable is ext3 compared to the other ones.

---

### Post by sagara on 2005-02-09
The file system that you should use really depends on what you intend to use your ubuntu system for.

For instance, if you are going to program in C (just to specify a language) then the reiserfs is your best option since it has been optimized to handle small files.  Which is what you as a programmer will use the most.

Here is a brief review of some of the file systems available

ext2: old yet reliable file system, the old default one.
ext3: enhanced version of ext2, use it if you are more of a multipurpose user
reiserfs: fast and optimized File System to handle small files
XFS: optimized file system to handle large files

Im new also to this so I cant really tell you what they mean by large files, but you can google out something like - ext3 reiserfs jtfs file system - and be sure to find lots of sites with in depth information.

---

### Post by ubuntu UsER on 2005-02-10
XFS = the best choice for me :)

---

### Post by Buffalo Soldier on 2005-02-10
Used to be reiserfs. But now ext3.

---

### Post by nocturn on 2005-02-10
reiser, I have been using it for years and never had any trouble with it (even run my servers on it).

---

