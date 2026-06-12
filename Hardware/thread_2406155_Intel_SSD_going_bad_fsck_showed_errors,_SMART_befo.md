---
title: "Intel SSD going bad? fsck showed errors, SMART before and after no errors."
date: 2018-11-16
forum: Hardware
---

### Post by Steve Goodey on 2018-11-16
Hello

I wonder if someone can help me?

My Mythbuntu box informed me of no recordings this morning, bit of a shock as there should be 750GB worth.

Anyway to cut a long story short the OS drive had errors. It's a 180GB Intel SSD bought just over a year ago! Rebooting the box showed me a (initramfs) prompt saying that /dev/sda2 had errors. After performing an fsck:- 
Inodes that were part of a corrupted orphan linked list were found so I OKd a fix.
A deleted inode had zero dtime, I OKd a fix.
Free blocks count was wrong, fixed.
Inode bitmap differences fixed.
Free inodes count wrong, fixed.

Another fsck after the above completed without errors.

A SMART run was done a week ago and completed OK.
Another one after the fsck also completed ok.

I've attached an image of the fsck output, was only able to get it as a photo on my mobile. Also attached are the SMART logs before and after the fsck.

Thanks for any advice.

[ATTACH=CONFIG]281653[/ATTACH][ATTACH]281655[/ATTACH][ATTACH]281654[/ATTACH]

---

### Post by Autodave on 2018-11-16
Just because fsck and SMART say it is OK, doesn't mean that it is OK.  With all of the errors that you had, I would say that either the disk is failed/failing or you had a power interruption while it was writing to the disk.  If there was a possibility of a power loss, then I would reformat it and start over.  Otherwise, looks like it is time to find another SSD.

---

### Post by rbmorse on 2018-11-16
Along the lines of what Dave said, also make sure the data and power cables are secure.  If your power supply uses modular cables for drive power, make sure the end that plugs into the PSU is fully seated, too.

---

