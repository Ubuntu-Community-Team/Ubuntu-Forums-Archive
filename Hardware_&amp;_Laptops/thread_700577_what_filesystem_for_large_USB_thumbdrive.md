---
title: "what filesystem for large USB thumbdrive ?"
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by dhuff on 2008-02-18
I suppose this problem counts as "an embarrassment of riches," but I recently bought an 8 GB USB thumbdrive that came formatted as vfat.

Problem is that I understand this filesystem can't be used for files over, I believe, 4 GB in size.  So what filesystem should I choose if I want to carry around files larger than that ? I'd also like to have the drive be a least readable on Win/Linux/Mac, and I'd prefer it to be writable under all three as well.

Is this a solvable problem ?

---

### Post by sadams on 2008-02-18
Good question.
I cannot give an authoratitive answer but I would also be interested to know this and also to extend the question to:
  - "external media in general"
&
  - USB hard drives in particular:
   I have a 40 GB external USB drive which I like to use for backups. Ideally I would like to backup my important filesystems/dirs to local hard-disk - then periodically copy the backups to the external drive.
I like to use (good old) "unix dump/restore" as my preferred backup method - resulting in single, seperate, large files (i,e. size of the used space in the filesystem dumped) which are "too big" to go on a dumb vfat drive (limit 2GB or 4GB"?).

Can I partition/format the USB device as I would any other disk - or is this reckless and foolhardy and likely to brick it?

Regards, Steve.

---

### Post by CaseyR on 2008-02-19
im dealing with this same issue right now.  i believe im going to reformat my external drive to ntfs.  i believe (with a little work) both linux and mac can read/write to ntfs.  somebody correct me if im wrong.

---

### Post by reacocard on 2008-02-19
> **CaseyR said:**
> im dealing with this same issue right now.  i believe im going to reformat my external drive to ntfs.  i believe (with a little work) both linux and mac can read/write to ntfs.  somebody correct me if im wrong.

that is correct. I believe mac handles it fine automatically, and most modern linux distros will as well (older distro versions usually can at least read with some tweaking). Ubuntu gutsy at least has near-perfect support for ntfs drives so if that's all you need, go for ntfs.

---

### Post by nisarg on 2008-03-15
i am going to need to reformat a 160gb external disk so that I can copy file bigger than 4gb. I am thinking of formatting it with NTFS. But this drive has a lot of data - so wanted to be double sure, is NTFS going to definately work? 
Does NTFS allows to copy across files larger than 4gb?
Is there limit at all with NTFS? If yes, how much?

thanks in advance for replies.

---

### Post by articpenguin on 2008-03-15
use a journalling filesystem and your thumbdrive will wear out faster.

---

### Post by nisarg on 2008-03-15
journalling filesystem?

> **articpenguin said:**
> use a journalling filesystem and your thumbdrive will wear out faster.

---

