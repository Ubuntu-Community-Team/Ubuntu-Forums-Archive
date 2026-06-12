---
title: "Gparted error in resizing ntfs partition.. why!?"
date: 2009-04-14
forum: Hardware
---

### Post by Afisamuleal on 2009-04-14
I am changing my partition scheme from one huge ntfs partition, one extended partition with an ext3 (ubuntu) partition it, and several now (after being backed up) deleted partitions.

From this:
[IMG]http://be.telge.us/e/partition/ptable.jpg[/IMG]

I get this error message when attempting to shrink the ntfs partition (Vista.. It has built in shrinking, but it doesn't let me shrink it enough or when I want to, it's crazy)
[IMG]http://be.telge.us/e/partition/error.jpg[/IMG]

Which isn't very helpful. I saved the logs to my flashdrive, but that has debian installed on it, and I can't access my ext2 home partition on it from WinXP here (my dad's computer, no ext recognizing drivers).

Basically, it's failing before it does anything. I took a picture.
[http://be.telge.us/e/partition/errorlarge.jpg]("http://be.telge.us/e/partition/errorlarge.jpg")

The first time I tried, it had an error message next to third thing, I think.. "check file system for errors and fix them".

So, any clues why this is failing?

---

### Post by cariboo on 2009-04-14
Did you defrag your NTFS at least twice before trying to resize it?

If you are running Vista, use it's disk maintenance tools to resize the partition.

Jim

---

