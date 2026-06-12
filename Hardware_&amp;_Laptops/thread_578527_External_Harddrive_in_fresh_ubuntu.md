---
title: "External Harddrive in fresh ubuntu"
date: 2007-10-17
forum: Hardware &amp; Laptops
---

### Post by gukarma on 2007-10-17
Here's the quick of my question:

I have an external harddrive that was originally used in a xp boot. It is ntfs. How do I use it in ubuntu 7.10? I don't want to format it fat32, since I am going to have very large files in it. 

Thanks,

Gustavo.

---

### Post by Kowalski_GT-R on 2007-10-17
Ubuntu's default filesystem is called ext3,

anyway, Gutsy Gibbon can read NTFS filesystems out of the box, so you should have no problems at all....

ciao,

Andre

---

### Post by gukarma on 2007-10-17
This is the message I get:

---

### Post by gukarma on 2007-10-17
Help? ;_;

---

### Post by gukarma on 2007-10-17
I am sorry for bumping this so much, but I am really lost in what to do.

---

### Post by urbushey on 2008-02-16
I am using Gutsy and I have much the same problem. 

Currently I am experimenting with trying to get something called ntfs-config installed, although package dependency problems are thwarting me somewhat.

Any other suggestions?

---

### Post by urbushey on 2008-02-16
I just found an old post that advised me to do this to get a read-only jump on the drive:

sudo mkdir /media/disk
sudo mount -t ntfs /dev/sdb1 /media/disk -o force

This worked well, and for my purposes a one-time read-only was all I needed. 

Others with this problem, I suggest you read-only, copy off everything you need, then format it to something more Linux compatible.

---

