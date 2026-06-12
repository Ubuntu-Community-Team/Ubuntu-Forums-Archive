---
title: "need help with installation - partitioning"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by stoneimplementor on 2009-02-06
hello, I recently got a new 1 TB hard drive and wanted to use it to install ubuntu on my computer.  When I installed the hard drive, I set apart a 10 GB partition that I would use to eventually install ubuntu on.  But when I tried installing it, the install program only gave me the option of using the large 990 GB partition, and wouldn't let me choose the partition that I set aside for it.  Is there anyway to install it on the partition I set aside?  Thanks for any help I can get on this.

---

### Post by Niniel on 2009-02-06
How's your disk set up?
I.e. how many partitions do you have already, and are they all primary partitions?

---

### Post by az on 2009-02-06
You have nothing else on this drive yet, correct?

Why not let the Ubuntu installer set up the partitions?  In Manual Partitioning, delete everything and create the partition scheme you want.

---

### Post by stoneimplementor on 2009-02-06
I partitioned the hard drive with two 10 GB partitions and a 990 GB partition, all primary. The largest partition I've already filled with about 100 GB of media, so I don't think I can have ubuntu partition it for me.

---

### Post by Niniel on 2009-02-06
> **stoneimplementor said:**
> I partitioned the hard drive with two 10 GB partitions and a 990 GB partition, all primary. The largest partition I've already filled with about 100 GB of media, so I don't think I can have ubuntu partition it for me.

No, but you can still resize it (with such a huge drive, why not give Ubuntu at least 20 GB?).
Have you tried manual partitioning? 
You could also try to delete the 10 GB partition first so that you just have 10 GB of free space into which to install Ubuntu. That might work better.

---

### Post by Reljoy on 2009-02-07
You have to be careful. I had win xp on my new drive and I had left 40GB to install Ubuntu into. During the install I was given some options and I didn't like the look of any of the them. I finally went for largest contiguous free space and Ubuntu installed right over the top of my windows xp. I was not happy. It seems that Ubuntu does not provide an option for using a spare part of the disk that you have left set aside specially to put Ubuntu on.

---

### Post by az on 2009-02-07
> **Reljoy said:**
> You have to be careful. I had win xp on my new drive and I had left 40GB to install Ubuntu into. During the install I was given some options and I didn't like the look of any of the them. I finally went for largest contiguous free space and Ubuntu installed right over the top of my windows xp. I was not happy. It seems that Ubuntu does not provide an option for using a spare part of the disk that you have left set aside specially to put Ubuntu on.

I'm sorry you had a bad experience.  But Ubuntu does provide that option.  If you specifically told it to use one partition and it installed on another, then that's a serious bug.

There are currently no critical bugs about partitioning:
[https://launchpad.net/ubuntu/+bugs?field.searchtext=partition&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://launchpad.net/ubuntu/+bugs?field.searchtext=partition&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

Usually, the partitioner will quit and do nothing instead of doing the wrong thing.

---

