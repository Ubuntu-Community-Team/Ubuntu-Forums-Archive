---
title: "Partitions"
date: 2008-09-14
forum: General Help
---

### Post by Tepear on 2008-09-14
I'm not 100% sure this is the correct area to post this question in - and if it isn't I'm sorry.

I reinstalled Ubuntu a few days ago and I looked up some information on the partitions. After reading through lots of information I decided to go with these, please give me any information as to how good or bad these are and if I can make them more effective please explain how :smile:

/dev/sda1 - /boot - reiserfs - 196.1 MiB
/dev/sda2 - swap - swap - 1512 MiB
/dev/sda3 - / - reiserfs 19.1 GiB
/dev/sda4 - /home - reiserfs 258.8 GiB

---

### Post by Jordanwb on 2008-09-14
Well I prefer to use ext2 for /boot (but that's just me), because since not a whole lot is done there you don't really need journaling. Also I don't think you need 1 1/2 GB of swap if you have at least 512MB of real RAM. Other than that it looks fine.

---

### Post by Tepear on 2008-09-14
> **Jordanwb said:**
> Well I prefer to use ext2 for /boot (but that's just me), because since not a whole lot is done there you don't really need journaling. Also I don't think you need 1 1/2 GB of swap if you have at least 512MB of real RAM. Other than that it looks fine.

I have ~756MB of real ram, and multiple websites said to double your ram and use that for your swap. If it really is to big should I decrease it? I am going for the best performance that I can get out of my computer.

Does having ext2 for /boot make any difference performance wise? Or is it more for looks?

---

### Post by Pro-reason on 2008-09-14
Personally, I'd be a bit more generous to the root partition, since you have plenty of space.  You haven't left much room for installing extra software, but that might not be important.

Also, although my root partition is reiserfs, my partition for my own files is ext3, so that it can be accessed by Windows if necessary, but again that might not be important.

It really doesn't matter much what filesystem you use for /boot.

The general advantage of ext2 over ext3 is that is can be defragged, and that Windows can't see ext3's journal.  The advantage of ext3 over ext2 is that it has the stability of journalling.

The &#8220;double RAM&#8221; thing for swap space is a strange old traditional Unix rule of thumb.  It doesn't make much sense.  One gig of swap for everyone is more sensible.  In fact, if you want to vary that, the amount of *hard drive* space you have is a better criterion for deciding how much of it you want to be eaten up by a swap partition which will mostly be doing nothing.

---

### Post by Tepear on 2008-09-14
Very helpful thanks! How would I go about editing my partitions to decrease/increase size? I'm still pretty new at all of this :smile:

---

### Post by Pro-reason on 2008-09-15
> **Tepear said:**
> Very helpful thanks! How would I go about editing my partitions to decrease/increase size? I'm still pretty new at all of this :smile:

Use Gparted.

But make sure that any important data is backed up before playing with partitions.

---

