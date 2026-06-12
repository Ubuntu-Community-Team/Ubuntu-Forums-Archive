---
title: "New disk formatted as ext3: 7GB in use?"
date: 2007-01-26
forum: Hardware &amp; Laptops
---

### Post by Breepee on 2007-01-26
Today my new 500GB hard disk was delivered, so I immedeately installed it. It is intended as a backup drive for mainly my music collection and some movies too. I want to format it as ext3, a no-nonsense filesystem. Since it isn't need, I set the reserved space for the superuser to 0% and I formatted is as follows:

mkfs.ext3 -m0 /dev/sdb1

Now the strange part: gparted reports that little over 7GB is in use, right after I formatted the drive. I tried to format with gparted, without setting the reserved blocks to 0%, gparted gives the same numbers. When I set the reserved blocks to 0% afterwards with tune2fs, still the same numbers. I tried all sorts of way's to format the drive, gparted keeps telling me 7GB is already in use. When I format the drive as fat32, only 230MB is in use, much better if you ask me. It's a big drive, but I want that 7GB ;)

So, what is going on here? Why is 7GB taken and what can I do about it? Is it possible a large amount is taken by inode tables? If so, what can I do about it? metadata on this drive is irrelevant and the number of files and directories on the drive will be, lets say, well below 1 million.

---

### Post by Breepee on 2007-01-26
I tried formatting with ext2 too, also shows 7.44GB taken up.

By the way, can I disable the lost+found folder?

---

### Post by taurus on 2007-01-26
If you format it to ext3, than 5% of the total space is reserved for root in case you fill up the harddrive and personally, I wouldn't remove lost+found directory.  That's where it will save some stuff to if there is a problem with your harddrive.

---

### Post by Breepee on 2007-01-26
> **taurus said:**
> If you format it to ext3, than 5% of the total space is reserved for root in case you fill up the harddrive and personally, 

That I already took care off by using -m0 as an arguments (explained in first post).

---

### Post by Breepee on 2007-01-27
Any thoughts? I can't find anything about the inodes, so maybe it's something else.

Update: formatting with

mkfs.ext3 -m 0 -T largefile4 /dev/sdb1   takes up 174MB (inode for every 4MB)

mkfs.ext3 -m 0 -T largefile /dev/sdb1     takes up 220MB (inode for every MB)

Since the drive is going to hold mostly FLACs (music db) I think I'll go with largefile. What are the disadvantages? How will smaller files be handled? Like mp3's of 2MB? will everyfile take up at least 1MB?

---

### Post by Enverex on 2007-01-27
Try using Reiser3 or Reiser4, those should give you only a tiny amount in use after formatting compared to ext3. You could try not using a Journal too, I think that may be the issue with ext3 for you, so try ext2.

---

