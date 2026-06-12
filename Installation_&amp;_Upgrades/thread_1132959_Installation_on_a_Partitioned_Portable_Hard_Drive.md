---
title: "Installation on a Partitioned Portable Hard Drive?"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by Pr0udDragon on 2009-04-22
Hi,

I have a 250 GB portable hard drive that I installed Ubuntu 8.04 Hardy Heron on and it was successfully dual-booted.  I did not partition it and I just installed it using the Wubi installer.  My problem is tomorrow, when Ubuntu 9.04 Intrepid Ibex comes out, I wan t to partition my portable hard drive and install Ubuntu 9.04 on there.  I want to partition it because I'm going to start working on video projects and I don't want Ubuntu to get slowed down because of a fragmented hard drive.

My question is this: how do I install Ubuntu 9.04 on a partition on a portable hard drive and how much space should I give it?  I want around 30 GB of space to use, mainly because I want to play my games on it.  Do I just partition it and make a 30 GB partition and select that for the install or is there more to it than that?

My other question mainly relates to partitions in general.  If I partition a portable hard drive, will it appear as another hard drive like my internal hard drive does?

Thank you, and sorry for all the questions, I'm new to this. :/

---

### Post by dandnsmith on 2009-04-22
I'm slightly confused about the part that wubi is playing in all this, but the partitions bit goes like:

You will already have one partition on the external drive, and what you want to do is add another (possibly squeezing what is already there).
A tool like gparted can do the partitioning bit - but you should back up the data on the disk first, in case of accident. Gparted (or whatever) can show you the single partition structure as it is now.

HTH

---

### Post by Pr0udDragon on 2009-04-22
Okay, thanks.  I was thinking Wubi because that is what I'm used to installing with, but installing from the Live CD doesn't seem too difficult.  I'm going to give it a go and get this thing ready for tomorrow or Friday, whenever I get a chance to try it.  I appreciate the quick reply. :)

EDIT: I forgot to ask, will I be able to install to an NTFS partition if I use the Live CD?  I'm just more comfortable NTFS because I'm used to it.

---

### Post by cubeist on 2009-04-22
NTFS is not a good file system, so even if you could (which you can't) why on earth would you want to.  Linux works on ext2,3,4 reiserfs, btrfs, etc...

---

### Post by Pr0udDragon on 2009-04-22
Okay, I read up on some stuff (I asked here because I was a little skeptical) and here's what I'm thinking (I haven't finalized any of this yet):

New Partition #1  Extended  31.38 GiB
New Partition #3  Ext3  29.42 GiB
New Partition #2  Linux-Swap  1.96 GiB

I have 1 GB of RAM on my computer right now.  Should I make my ext3 partition bigger so I don't have to worry about having to edit it later, and are these good partitions?  Thanks for the info.

One last thing, should I wait until 9.04 comes out and use the ext4 file system instead?  Thanks.

---

### Post by cubeist on 2009-04-22
Two things, first, ubuntu won't really slow down from fragmentation. Linux filesystems are different from windows, and fragmentation is a windows phenomenon.

Second, since you don't need a partition for your video files, why not just upgrade to jaunty?

Third, if you are doing a fresh install, and want the latest and greatest file system, you should think about ext4

---

### Post by Pr0udDragon on 2009-04-22
Okay, thanks a lot!

So you're saying that, even if I use the Wubi installer, it won't get slowed down by fragmentation?  I just want that cleared up for me.

I tried upgrading from Hardy to Intrepid, but the updater would not do a thing about it.  Later on in the installation it got an error on probably half the files and completely messed it up.  So bad that I couldn't even access the updater and the main file viewer, only my /home folder.  I really only had a bunch of themes on there, since I was still messing around with it and getting it the way I liked it.

I think this should be about the last question for me (thanks a lot for all the quick replys; you all are extremely helpful and friendly!): Since I'm a little skeptical about partitioning (I don't have any real experience with it, only basic stuff), would it be best to do a clean install with Wubi under Windows?  Thanks.

---

### Post by cubeist on 2009-04-22
I can't comment on wubi usage, as I have never used it, but there are quite a few threads here on the ubuntu forums regarding wubi usage.  Whether you install via wubi or clean install, you won't have fragmentation issues... this is a windows mindset problem.

IMO, a clean install is always preferable to an update, but sometimes people have partitions the way they like and upgrading is the best solution.  Also, if you are not comfortable with partitioning schemes, upgrading is probably the best bet.

---

### Post by Pr0udDragon on 2009-04-22
Okay, that pretty much solves my problems.  Thanks a lot!  I'm going to hold my excitement in until tomorrow and I'm going to do a clean install of Ubuntu 9.04.  Once again, sorry for all the questions and thanks for being patient with me.  I will check out the threads and know exactly what I need to know afterward.  Jaunty is going to be awesome.

---

### Post by cubeist on 2009-04-22
Jaunty is awesome! A nice step forward for open-source.

Post back if you have more partition questions, we don't want you accidentally deleting the wrong partition!

---

### Post by Pr0udDragon on 2009-04-22
I will, thanks!  I do have a question though: if I install the test version of Jaunty, will I be able to update it to the full version tomorrow?

---

### Post by cubeist on 2009-04-22
of course, just download the latest daily-live cd and in a couple days perform all the updates available in the update-manager and your system will be identical to the final version.

---

### Post by Pr0udDragon on 2009-04-22
Sweet!  Thanks a lot!  I actually didn't think it would be as easy as updating the test version, so I didn't do it.  I'm going to start the download right now so it's done by tomorrow.  I hope Jaunty is as good as everybody says it is! :guitar:

---

