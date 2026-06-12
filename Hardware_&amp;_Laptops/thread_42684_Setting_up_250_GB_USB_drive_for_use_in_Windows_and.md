---
title: "Setting up 250 GB USB drive for use in Windows and Linux"
date: 2005-06-19
forum: Hardware &amp; Laptops
---

### Post by timelord726 on 2005-06-19
Hi all,

I have two questions that relate and lead back to the same situation.  I have a new 250 GB USB drive (currently with a single partition formatted as NTFS) and I want to set it up as a drive that both Windows and Linux can read from and write to with as little hassle as possible.

Question 1: what would be the best way to set this up, as far as partitions and file systems go?

Question 2: how would I go about implementing the answer to question 1 from within Linux?  This is just a laziness or personal preference thing, so it's not as important as question 1, as long as I know how to do it somehow.

Thanks in advance for all your help!

---

### Post by mtron on 2005-06-19
- filesystem: for Linux and Win read / write access use vfat system, to make it, use qparted, make your partitions and format them.

- partitions: i suggest 2 -3 partitions. one for backup of your build in harddisk, one for documents / work and one for music & videos. 

about vfat see [here](http://www.ubuntuforums.org/showthread.php?t=39486)

---

